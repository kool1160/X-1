# X-1 System Architecture

## Mechanical stack

```text
CrossFire PRO external envelope and assembly relationships
                |
Structural steel tube lower frame, legs, stanchions, gussets, and skirts
                |
Zinc-plated Y tube rails
                |
Adjustable fixed/eccentric rolling-bearing Y carriages
                |
CrossFire PRO gantry tube and rolling X carriage
                |
3/8-8 4-start Y ACME screws + 1/2-10 5-start X ACME screw
                |
NEMA 23 X/Y motors, couplers, floating anti-backlash nuts, 608 supports
                |
Powered floating Z, torch mount, IHS, and position-aware THC correction

Internal structure:
stainless water tray -> slat holders -> slats -> workpiece
```

The standard CrossFire PRO assembly guide and published PRO dimensions are the mechanical authority. PRO MAX, profile rails, and ball screws are not part of the active baseline.

## Replica boundary

### Mechanically reproduced

- frame and floor-space geometry
- tube rails, stanchions, and adjustable rolling carriages
- gantry and X carriage
- ACME lead screws, anti-backlash nuts, couplers, supports, and motors
- water tray, drains, slats, and holders
- floating powered Z and IHS mechanism

### Replaced by X-1

- Langmuir control electronics
- FireControl and Langmuir computer
- OEM electronics enclosure internals
- LS-THC and OEM voltage interface

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
CrossFire PRO-equivalent X / Y-left / Y-right / Z mechanics
                |
isolated Everlast plasma interface
```

X-1 Control owns the operator workflow, visualization, jobs, material profiles, alarms, diagnostics, logging, and THC controls. FluidNC owns real-time motion and controller-side THC functions. Hardwired safety remains independent of both software layers.

## Motion-channel assignment

| Channel | Function | Mechanical axis |
|---|---|---|
| X | X carriage | 1/2-10, 5-start ACME; 0.5 in/rev |
| Y | Y-left | 3/8-8, 4-start ACME; 0.5 in/rev |
| A | Y-right | 3/8-8, 4-start ACME; 0.5 in/rev |
| Z | Torch height | Powered floating Z, IHS, THC correction |
| B | Reserved | Controlled future use only |
| C | Reserved | Controlled future use only |

Final socket assignment and GPIO mapping must be verified against the actual Jackpot board and FluidNC build.

## Machine signal flow

```text
X-1 Control
   |
   | commands, jobs, settings, status, logs
   v
Jackpot + FluidNC / X-1 fork
   |
   |-- motor channels ---------------------> X, Y-left, Y-right, Z
   |-- digital inputs ---------------------> homes/limits, float/IHS, E-stop status
   |-- isolated output --------------------> Everlast torch-start dry contact
   |<-- isolated input --------------------- Everlast Arc OK
   |<-- isolated voltage interface -------- Everlast divided arc voltage
   |
   `-- THC status/control -----------------> X-1 Control
```

No raw or divided arc-voltage signal may connect directly to Jackpot or ESP32 GPIO.

## Mechanical alignment sequence

1. Loosely assemble and square the lower tube frame.
2. Hold lower rail spacing and Y-rail parallelism within 1/32 in.
3. Assemble fixed/adjustable rolling-bearing carriages.
4. Install Y tube rails through carriages and stanchions.
5. Assemble gantry, X carriage, powered Z, motor mount, and bearing mount.
6. Attach gantry to both Y carriages with fasteners loose.
7. Preload carriage bearings with minimum force that removes play.
8. Move gantry against common stanchion references and lock carriage/gantry relationships.
9. Install floating lead nuts, ACME screws, support bearings, couplers, and motors.
10. Tighten couplers with motors energized for holding torque.
11. Square the mechanism, then tighten floating lead nuts.
12. Cycle every axis through full travel and verify the published envelope.

## Staged operating sequence

### Commissioning baseline

1. Home/square the machine.
2. Move to pierce location.
3. Probe material with the floating IHS head.
4. Retract to pierce height.
5. Close isolated torch-start.
6. Confirm Arc OK and complete pierce delay.
7. Move to fixed cut height.
8. Execute toolpath with THC disabled.
9. Open torch-start.

### Required production sequence

1. Perform home, probe, pierce, and cut-height sequence.
2. Enable THC only after Arc OK, stabilization delay, and valid velocity conditions.
3. Measure isolated arc voltage and compare with target.
4. Apply position-aware Z correction within limits.
5. Suspend correction during corners, slowdowns, invalid voltage, cut loss, or anti-dive conditions.
6. Report live voltage, target, active/inhibited state, corrections, and faults to X-1 Control.
7. Preserve correct Z position through hold, resume, reset, Arc OK loss, and recovery.

## Electrical zones

- **AC/mains:** disconnect, contactor/safety relay, protected supplies.
- **Motor power:** Jackpot supply and external drives if required.
- **Controller:** Jackpot, service USB/network, low-voltage distribution.
- **Plasma interface:** isolated torch relay, Arc OK isolation, voltage isolation/protection, optional THC co-processor.
- **Field terminals:** motors, switches, cable routing, grounding/bonding.

## Data and configuration

The repository will contain:

- source-evidence matrix for replica dimensions;
- SolidWorks assembly and released drawings;
- DXF cut files;
- ACME screw machining drawings;
- motion BOM and supplier records;
- FluidNC configuration and controlled fork if needed;
- pin/I/O map and terminal schedule;
- THC hardware/firmware/protocol/settings;
- X-1 Control source and database schema;
- alignment, calibration, motion, plasma, and THC test records;
- as-built photographs and documented deviations;
- known-good releases and rollback information.
