# FluidNC Workspace

The X-1 prototype uses the V1 Engineering Jackpot CNC Controller V1.2.1 running FluidNC or a controlled X-1 FluidNC fork required to deliver the locked machine requirements.

## Intended machine channels

- X carriage
- Y-left
- Y-right
- Z torch height, probing, and position-aware THC correction
- two spare channels reserved until formally assigned

## Configuration release rule

Do not commit a claimed working `machine.yaml` until the following are verified on the actual board and machine:

- installed FluidNC version and exact build identity;
- Jackpot board revision and ESP32 module;
- driver-socket assignment;
- step/direction method for onboard or external drivers;
- motor current and microstep settings;
- exact home, float/probe, E-stop-status, torch-output, Arc OK, and selected THC-interface pins;
- switch active state and pull-up/pull-down behavior;
- steps per millimeter;
- travel limits;
- homing direction and sequence;
- Y-left/Y-right squaring behavior;
- maximum velocity and acceleration;
- THC firmware boundary, configuration fields, status fields, and failure behavior.

## Commissioning configurations

Keep separate known-good configurations for:

1. **Motion bench:** motors and switches only; no plasma connection.
2. **Fixed-height machine:** homing, probing, isolated torch start, and Arc OK; THC correction disabled.
3. **THC simulator:** safe low-voltage input simulator and position-aware Z correction; plasma disconnected.
4. **Live THC:** released production configuration after live validation.

Do not overwrite a known-good stage with an unproven later-stage configuration.

## Commissioning sequence

1. Save the original Jackpot configuration and firmware information.
2. Power the controller from the verified 9–24 V supply with plasma disconnected.
3. Test one motor channel at a time at low current and low speed.
4. Test inputs by hand through the documented status interface.
5. Verify axis directions and travel limits.
6. Configure independent Y homing and repeated squaring tests.
7. Run dry G-code before connecting torch start.
8. Add the isolated torch-start relay.
9. Add Arc OK only through a verified isolated interface.
10. Add the selected isolated voltage interface first to a safe signal simulator.
11. Prove position-aware THC correction during simultaneous X/Y motion.
12. Establish live fixed-height cutting before enabling correction.
13. Enable and validate live THC according to `docs/THC_ARCHITECTURE.md`.

## Controlled firmware work

Upstream FluidNC does not currently provide a released, proven X-1 THC solution. Any custom THC work must:

- live in a clearly identified X-1 fork or patch set;
- record the exact upstream base commit/release;
- include source, build instructions, configuration schema, and tests;
- preserve Z machine-position tracking;
- define controller ownership during THC-active motion;
- expose voltage, Arc OK, enable, active, inhibit, correction, and fault status to X-1 Control;
- include safe behavior for hold, resume, reset, E-stop, signal loss, and restart;
- remain reproducible without relying on an undocumented local binary.

## Files planned here

- `machine.yaml` — released production configuration
- `machine.example.yaml` — commented development copy
- `PIN_MAP.md` — Jackpot socket/GPIO/terminal map
- `CALIBRATION.md` — steps, speeds, accelerations, and test results
- `THC_CONFIG.md` — selected THC fields, defaults, units, and allowed ranges
- `FIRMWARE_BASE.md` — upstream version/commit and X-1 patch/fork identity
- `backup/` — known-good staged configuration snapshots
- `patches/` or fork reference — controlled X-1 FluidNC changes when required

Never connect the Everlast raw or divided arc-voltage output directly to Jackpot or ESP32 GPIO.
