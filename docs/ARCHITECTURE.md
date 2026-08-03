# X-1 System Architecture

## Mechanical stack

```text
Removable exterior skins and guards
                |
Welded tube structural frame
                |
Adjustable rail pads / mounting faces
                |
Purchased X/Y linear guides and metal trucks
                |
Independent Y-left and Y-right drive systems
                |
Lightweight tube gantry with X guide and drive
                |
Metal Z slide, torch mount, probing mechanism, and THC correction

Separate internal structure:
water pan -> slat holders -> slats -> workpiece
```

The water pan and slats sit inside the structural frame but do not define rail alignment.

## Control layers

```text
X-1 Control — dedicated Windows operator application
                |
USB serial or network transport
                |
Jackpot controller running FluidNC / controlled X-1 fork
                |
real-time motion, homing, limits, probing, torch command, THC state
                |
X / Y-left / Y-right / Z motors and isolated plasma interface
```

X-1 Control owns the operator workflow, visualization, jobs, material profiles, alarms, diagnostics, logging, and THC controls. FluidNC owns real-time motion and any controller-side THC functions. Hardwired safety remains independent of both software layers.

## Motion-channel assignment

The Jackpot has enough driver positions for the intended machine layout. The conceptual assignment is:

| Channel | Function | Notes |
|---|---|---|
| X | X carriage | Gantry-axis motion |
| Y | Y-left | Independent homing switch |
| A | Y-right | Independent homing switch; slaved during normal motion |
| Z | Torch height | Probe, pierce height, cut height, and position-aware THC correction |
| B | Reserved | Future accessory or THC test hardware only when formally approved |
| C | Reserved | Future accessory or test channel |

Final socket assignment and GPIO mapping must be verified against the exact Jackpot documentation, installed board revision, and selected FluidNC build before wiring.

## Machine signal flow

```text
X-1 Control
   |
   | commands, jobs, settings, status, logs
   v
Jackpot + FluidNC / X-1 fork
   |
   |-- step/direction or onboard drivers --> X, Y-left, Y-right, Z
   |-- digital inputs ---------------------> homes, limits, float/probe, E-stop status
   |-- isolated output --------------------> Everlast torch-start dry contact
   |<-- isolated input --------------------- Everlast Arc OK
   |<-- isolated voltage interface -------- Everlast divided arc voltage
   |
   `-- THC status/control -----------------> X-1 Control
```

No raw or divided arc-voltage signal may connect directly to Jackpot or ESP32 GPIO.

## Staged operating sequence

### Commissioning baseline

1. Home and independently square Y.
2. Move to pierce location.
3. Probe material with the floating head or approved probe method.
4. Retract to pierce height.
5. Close the verified isolated torch-start contact.
6. Confirm Arc OK and complete the pierce delay.
7. Move to fixed cut height.
8. Execute the toolpath with THC correction disabled.
9. Open torch-start at the end of the cut.

This stage separates motion, probing, CAM, torch, and plasma-interface faults.

### Required production sequence

1. Complete the same home, square, probe, pierce, and cut-height sequence.
2. Enable THC only after Arc OK, stabilization delay, and valid motion conditions.
3. Measure isolated arc voltage and compare it to the selected target.
4. Apply position-aware Z correction within configured rate and travel limits.
5. Suspend correction during corners, slowdowns, invalid voltage, cut loss, or other anti-dive conditions.
6. Report live voltage, target, enabled/active state, corrections, Arc OK, and faults to X-1 Control.
7. Disable correction before lead-out/end-of-cut behavior requires fixed Z ownership.
8. Preserve correct Z machine position through hold, resume, reset, Arc OK loss, and fault recovery.

The finished machine is not complete without this production sequence passing validation.

## THC subsystem boundary

The exact architecture remains open and is controlled by `THC_ARCHITECTURE.md`. The leading investigation is an integrated X-1 FluidNC THC module, with a dedicated co-processor as the second path if analog/noise or resource limits require it.

Regardless of implementation, the subsystem consists of:

- verified Everlast divided-voltage and Arc OK signals;
- galvanically isolated and protected measurement/interface hardware;
- real-time control close to the motion controller;
- position-aware Z correction;
- anti-dive and fault logic;
- X-1 Control commands, visualization, diagnostics, and logs.

A standalone THC that directly steals Z control is not acceptable unless every correction remains synchronized with FluidNC position and control handoff is proven fail-safe.

## Electrical zones

The enclosure should be divided into functional zones:

- **AC/mains:** disconnect, contactor/safety relay, protected power supplies.
- **Motor power:** 24–48 VDC supply and external drivers if selected.
- **Controller:** Jackpot, USB/network service access, low-voltage distribution.
- **Plasma interface:** isolated torch relay, Arc OK isolation, divided-voltage isolation/protection, and optional THC co-processor.
- **Field terminals:** motors, switches, cable-chain wiring, grounding/bonding.

Torch lead, work lead, motor power, mains, step/direction, switch, and voltage-measurement wiring should be separated wherever practical.

## Data and configuration

The repository will contain:

- released SolidWorks models and drawings;
- DXF cut files;
- selected-component records and released BOMs;
- FluidNC machine configuration and any controlled X-1 fork;
- pin/I/O map and terminal schedule;
- THC hardware, firmware, settings, and protocol definition;
- X-1 Control source and database schema;
- driver-current and microstep settings;
- calibration, communication, motion, plasma, and THC test records;
- photographs and documented as-built changes;
- known-good release tags and rollback information.
