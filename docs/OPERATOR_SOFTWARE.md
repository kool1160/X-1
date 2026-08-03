# X-1 Operator Software Architecture

## Purpose

X-1 requires complete machine-operating software, not a generic G-code sender. The operator must be able to turn on the machine, connect, home, square the gantry, load a job, position it on the sheet, verify the cut, run it with THC, recover from interruptions, and diagnose faults without opening a generic terminal or switching among unrelated utilities.

## Two-layer control model

### Layer 1 — Jackpot and FluidNC

FluidNC or a controlled X-1 FluidNC fork owns time-critical machine functions:

- step generation;
- coordinated X/Y/Z motion;
- independent Y-left/Y-right homing;
- hard and soft limits;
- probe and control inputs;
- real-time hold, resume, reset, and status reporting;
- local file execution;
- low-level torch-output command after the interface is verified;
- controller-side THC behavior selected by `THC_ARCHITECTURE.md`.

### Layer 2 — X-1 operator application

The X-1 application runs on a dedicated Windows machine PC and owns the operator workflow:

- machine discovery and connection;
- setup and configuration backup;
- plasma-specific controls and state display;
- G-code import, parsing, validation, and visualization;
- material and cut-profile database;
- sheet setup and work offsets;
- job queue and job history;
- perimeter trace and dry run;
- probing and pierce workflow;
- job start, pause, resume, stop, and recovery;
- live arc voltage, target voltage, THC enable/disable, state, faults, and logs;
- alarms, diagnostics, maintenance records, and configuration history.

## Recommended first implementation

The leading implementation candidate is a Windows desktop application built with:

- **Tauri** for the desktop shell and native packaging;
- **React and TypeScript** for the operator interface;
- a local application service for FluidNC communication, file storage, logging, and machine-state handling;
- SQLite for material profiles, jobs, settings, and logs;
- SVG or Canvas-based toolpath visualization.

This direction is not locked until a small communication proof of concept is completed. A .NET desktop application remains a valid alternative.

## Communication paths

The application should support:

1. **USB serial** for commissioning, recovery, firmware/configuration work, and deterministic local service.
2. **Network connection** for normal operator use when reliable, using the approved FluidNC status and command interfaces.

The communications layer must be isolated behind an internal adapter so the user interface is not tied directly to one transport.

```text
X-1 UI
  |
Machine service and state engine
  |
FluidNC adapter
  |--------------------|
USB serial        network transport
  |                    |
Jackpot running FluidNC / X-1 fork
```

THC correction must not depend on round-trip communication through the Windows application. The operator software commands, displays, configures, and logs THC; the real-time loop remains at the controller or approved co-processor layer.

## Job execution strategy

The preferred normal workflow is:

1. Import G-code into the X-1 application.
2. Parse and validate it locally.
3. Display the toolpath and calculated bounds.
4. Check it against the configured work envelope and safe Z/THC behavior.
5. Select the material profile, cut settings, and approved THC settings.
6. Upload the approved job to controller storage.
7. Start the stored job through FluidNC.
8. Monitor progress, arc voltage, THC state, alarms, and controller messages.

This avoids making smooth motion depend on continuous Wi-Fi line streaming. Direct streaming may remain a test/service path but cannot be the only production path.

## Minimum machine-console release

### Machine screen

- connection status;
- controller and firmware identity;
- machine state: disconnected, idle, homing, running, hold, alarm, E-stop;
- X/Y/Z machine and work coordinates;
- home and square command;
- jog controls with selectable step size and continuous jog;
- zero X, zero Y, zero XY, and set work origin;
- switch-state panel;
- torch-output and Arc OK state display;
- feed hold, resume, stop, and reset.

### Job screen

- open G-code;
- toolpath preview;
- job dimensions and estimated bounds;
- detected errors and unsupported commands;
- origin selection;
- perimeter trace;
- dry run with torch inhibited;
- upload and start;
- progress and current path position;
- elapsed and estimated remaining time.

### Plasma and THC screen

- material name and thickness;
- amperage and consumable notes;
- cut speed;
- pierce delay;
- pierce height;
- cut height;
- kerf and CAM notes;
- Arc OK requirement;
- THC target voltage;
- THC delay and correction limits approved by the selected architecture;
- THC enable/disable;
- live arc voltage;
- enabled, active, inhibited, and fault states;
- reason for anti-dive or inhibition;
- voltage and correction history for diagnostics.

THC fields may remain disabled during early commissioning, but they are required before the production release.

### Diagnostics screen

- raw controller messages;
- input and output states;
- homing results;
- alarm history;
- configuration backup and restore;
- communication statistics;
- firmware/configuration versions;
- motor calibration results;
- Arc OK and voltage-interface state;
- THC configuration, state transitions, corrections, inhibits, and faults.

## Safety boundaries

The application may request motion, torch operation, and THC state changes but cannot be the only safety layer.

- E-stop must remove motion and torch-enable capability in hardware.
- Torch-start and plasma inputs must remain isolated.
- The application must clearly display when the torch is armed.
- Dry-run mode must inhibit torch firing through a verified mechanism.
- Software limits supplement but do not replace physical stops.
- Communication loss during a job must have a defined controller-side response.
- Loss of the operator application cannot leave THC or torch control in an undefined state.

## Development stages

### Stage 1 — Communication proof

- connect over USB;
- read startup and status messages;
- issue status, home, jog, hold, resume, and reset commands;
- display coordinates and controller state;
- log all traffic;
- add the network transport after USB behavior is understood.

### Stage 2 — Machine console

- add switch-state display;
- add dual-Y homing workflow;
- add work offsets and jogging;
- add configuration backup;
- package as an installable Windows application.

### Stage 3 — Job system

- local G-code parser and preview;
- bounds and safety checks;
- upload to controller storage;
- stored-file start and progress monitoring;
- job history.

### Stage 4 — Plasma workflow

- material profiles;
- probing and pierce sequence controls;
- torch/Arc OK state;
- perimeter trace and dry run;
- plasma-specific alarms and cut recovery.

### Stage 5 — Required THC operation

- live voltage and Arc OK display;
- target voltage and validated configuration controls;
- enable/disable and status handling;
- anti-dive/inhibit reason display;
- voltage, feed, correction, and fault logging;
- hold, resume, reset, cut-loss, and recovery behavior;
- configuration backup and compatibility checks with the installed THC firmware/hardware.

### Stage 6 — Maintenance and optional extensions

- maintenance counters;
- consumable tracking;
- optional pendant or touchscreen layout.

Optional extensions cannot delay the required machine, job, plasma, and THC workflow.

## Definition of done

X-1 operator software is production-ready only when an operator can perform the normal machine, job, plasma, and THC workflow without using the stock FluidNC WebUI, a generic G-code sender, or a terminal, while retaining a documented service path for low-level troubleshooting.
