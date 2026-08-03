# X-1 THC Architecture

## Requirement

The finished X-1 requires automatic closed-loop torch-height control based on arc voltage. Fixed-height cutting is an intermediate commissioning mode, not the final machine capability.

The THC system must work with the X-1 control stack:

- Everlast PowerPlasma 82i
- isolated plasma interface
- Jackpot controller
- FluidNC or a controlled X-1 FluidNC fork
- Z-axis motor and driver
- dedicated X-1 operator software

## Current FluidNC status

As of 2026-08-02, upstream FluidNC does not provide a documented, released, production-proven path for a conventional external THC to override the Z axis during coordinated motion.

Relevant upstream discussions:

- FluidNC issue #1105 requests a real-time axis override for external THC and remains open: https://github.com/bdring/FluidNC/issues/1105
- FluidNC issue #1746 proposed an integrated arc-voltage THC module, status reporting, anti-dive, and synchronized enable/disable. The issue was closed without an attached upstream pull request or released implementation: https://github.com/bdring/FluidNC/issues/1746

Therefore X-1 cannot assume stock FluidNC already solves THC. The project must select, implement, and validate a specific architecture.

## Required functions

The selected THC must provide:

- isolated arc-voltage measurement;
- verified voltage scaling and polarity;
- Arc OK gating;
- target-voltage setpoint;
- deadband or equivalent stable control region;
- real-time up/down Z correction;
- correct internal Z position tracking;
- enable and disable synchronized with the cut program;
- delay after arc establishment;
- corner and velocity anti-dive;
- response to kerf crossing, cut loss, and voltage outside plausible limits;
- maximum correction rate and Z travel limits;
- manual THC disable and operator override;
- live arc voltage, Arc OK, enabled/active state, and fault reporting to X-1 Control;
- deterministic safe response to sensor, firmware, communication, or controller faults.

## Signal chain

```text
Everlast divided arc voltage
          |
verified DV+ / DV- and divider ratio
          |
isolated, protected voltage interface
          |
THC measurement input
          |
real-time control loop near the motion controller
          |
Z correction through a position-aware motion path
          |
Z motor and mechanical slide

Everlast Arc OK
          |
verified isolated digital interface
          |
THC enable gate and X-1 status
```

No raw or divided arc-voltage signal may connect directly to a Jackpot or ESP32 GPIO.

## Candidate architectures

### Option A — Integrated X-1 FluidNC THC module

An X-1-controlled FluidNC fork reads the isolated arc-voltage signal, applies the THC control loop, and injects Z correction through FluidNC's motion/step engine while keeping machine position correct.

**Advantages**

- best integration with motion state and Z position;
- synchronized enable/disable can be implemented at toolpath boundaries;
- anti-dive can use commanded and actual motion state;
- status can be sent directly to X-1 Control;
- no separate controller fighting FluidNC for the Z motor.

**Risks**

- custom real-time firmware development and long-term maintenance;
- ESP32 ADC and plasma-noise performance must be proven or replaced by a better isolated measurement interface;
- concurrency with the existing step engine must be tested under worst-case motion;
- a proposed upstream design is not the same as validated production code.

**Decision requirement**

Build a bench proof that reads a simulated isolated voltage, reports it, and corrects Z during X/Y motion without losing position or corrupting motion.

### Option B — Dedicated THC co-processor with a defined FluidNC real-time interface

A separate microcontroller or THC module performs voltage measurement and control. FluidNC is modified only enough to accept validated real-time Z correction commands or up/down/rate information through a position-aware interface.

**Advantages**

- separates noisy analog measurement and control-loop work from the Jackpot;
- dedicated hardware can provide better ADC, isolation, and filtering;
- FluidNC modification may be smaller than a complete THC implementation.

**Risks**

- a real-time axis-override interface does not currently exist as a proven upstream feature;
- communication latency, synchronization, and failure behavior must be deterministic;
- both processors must agree on Z position and control ownership.

**Decision requirement**

Prove the full latency and failure behavior. Loss of the co-processor link must disable correction safely without corrupting Z position.

### Option C — Standalone external THC directly controlling the Z driver

A conventional THC receives arc voltage and Arc OK, then takes temporary control of the Z step/direction signals or uses an electrical selector/multiplexer around the Z driver.

**Advantages**

- commercial standalone THC hardware may be available;
- less analog and control-loop firmware development inside FluidNC.

**Risks**

- FluidNC can lose knowledge of actual Z movement;
- control handoff and step counting can drift;
- electrical multiplexing around step/direction is safety-critical;
- edge cases during hold, resume, reset, probing, or cut loss can create crashes;
- integration into X-1 Control may be limited.

**Decision requirement**

This option is not acceptable unless every THC step is reconciled with FluidNC position and the handoff is proven under reset, hold, communication loss, and power interruption.

### Option D — Controller migration contingency

Move the machine to a controller with a mature plasma/THC implementation only if FluidNC cannot pass the required bench and machine tests.

This is a contingency, not an active redesign. It requires a documented failure against X-1 requirements and a formal decision change.

## Current preferred investigation order

1. **Option A:** test an integrated X-1 FluidNC THC module because it offers the cleanest position-aware system and best operator-software integration.
2. **Option B:** evaluate a co-processor if the Jackpot's analog/noise performance or available resources are unsuitable.
3. **Option C:** use only if position reconciliation and fail-safe handoff are fully solved.
4. **Option D:** reopen the controller decision only after documented failure of the FluidNC paths.

This order is an investigation priority, not a final architecture decision.

## Measurement interface work

Before selecting the voltage-input hardware:

1. verify the Everlast CNC connector pinout;
2. verify DV+ and DV- polarity;
3. verify the physical 16:1 and 50:1 divider behavior;
4. measure open-circuit and loaded divided voltage;
5. reproduce and explain the observed behavior where the displayed voltage changed when the external meter was connected;
6. establish maximum expected signal and transient conditions;
7. select an isolated interface with adequate common-mode and surge protection;
8. compare its output to a trusted meter and simulated test source before connection to the controller.

## Bench proof sequence

### THC-0 — Safe signal simulator

- use a low-voltage isolated source to simulate divided arc voltage;
- sweep the signal through expected operating values;
- prove scaling, filtering, status reporting, open-wire detection, and overrange behavior.

### THC-1 — Z correction bench

- run X/Y motion with the plasma disconnected;
- vary the simulated voltage above and below target;
- verify correction direction, rate limits, deadband, and Z position tracking;
- test hold, resume, reset, E-stop, Arc OK loss, signal loss, and controller restart.

### THC-2 — Dry machine integration

- install the final Z hardware and limits;
- run complete G-code with simulated arc voltage;
- verify anti-dive during corners, slowdowns, holes, and lead-outs;
- verify synchronized THC enable and disable.

### THC-3 — Live fixed-height baseline

- establish stable probing, pierce, cut height, torch control, and Arc OK without THC correction;
- record physical arc voltage and cut behavior;
- confirm the voltage interface does not alter the plasma divider output.

### THC-4 — Live THC validation

- begin with straight cuts and conservative correction limits;
- test controlled material slope and warp;
- test corners, holes, kerf crossings, cut loss, and end-of-cut behavior;
- compare commanded and measured torch height;
- verify no torch dive and no accumulated Z-position error;
- record voltage, Z correction, feed rate, Arc OK, and fault logs.

## Architecture decision gate

The THC architecture can be locked only when the project has:

- a verified Everlast voltage/Arc OK interface definition;
- a selected isolated measurement method;
- a proven position-aware Z correction path;
- defined anti-dive and fault behavior;
- a clear firmware ownership and maintenance plan;
- a status/control interface for X-1 Control;
- bench evidence that the chosen path can pass the required failure tests;
- a complete cost and parts list.

## Final release gate

X-1 is not considered complete until THC maintains usable torch height over representative warped material without diving, losing Z position, corrupting motion, or requiring a generic sender or terminal for normal operation.
