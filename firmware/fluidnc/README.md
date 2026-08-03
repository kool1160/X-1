# FluidNC Workspace

The X-1 prototype will use the V1 Engineering Jackpot CNC Controller V1.2.1 running FluidNC.

## Intended machine channels

- X carriage
- Y-left
- Y-right
- Z torch height
- two spare channels for future use

## Configuration release rule

Do not commit a claimed working `machine.yaml` until the following are verified on the actual board and machine:

- installed FluidNC version;
- driver-socket assignment;
- step/direction method for onboard or external drivers;
- motor current and microstep settings;
- exact home, float/probe, E-stop-status, torch-output, and Arc OK pins;
- switch active state and pull-up/pull-down behavior;
- steps per millimeter;
- travel limits;
- homing direction and sequence;
- Y-left/Y-right squaring behavior;
- maximum velocity and acceleration.

## Commissioning sequence

1. Save the original Jackpot configuration and firmware information.
2. Power the controller from the verified 9-24 V supply with plasma disconnected.
3. Test one motor channel at a time at low current and low speed.
4. Test inputs by hand in the FluidNC status interface.
5. Verify axis directions and travel limits.
6. Configure independent Y homing and repeated squaring tests.
7. Run dry G-code before connecting torch start.
8. Add the isolated torch-start relay.
9. Add Arc OK only through a verified isolated interface.
10. Keep arc-voltage THC outside the first machine configuration.

## Files planned here

- `machine.yaml` - released machine configuration
- `machine.example.yaml` - commented development copy
- `PIN_MAP.md` - Jackpot socket/GPIO/terminal map
- `CALIBRATION.md` - steps, speeds, accelerations, and test results
- `backup/` - known-good configuration snapshots

Never connect the Everlast divided-voltage output directly to Jackpot GPIO.
