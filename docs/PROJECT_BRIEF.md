# X-1 Project Brief

## Mission

Design and build a low-cost, serviceable CNC plasma table that uses Chris Hilton's available steel and fabrication resources while avoiding the proprietary-controller and difficult-diagnostics problems of the current MyPlasm system.

## Machine identity

- **Project:** X-1
- **Meaning:** Laser X Design 1
- **Machine type:** CNC plasma cutting table
- **Primary use:** signs, sheet-metal profiles, fabrication parts, and prototype work
- **Nominal width:** 48-inch cutting capacity
- **Nominal length:** component-driven; target approximately 60-72 inches

## Build philosophy

1. Use free 1/8-inch-wall tube for the structural frame.
2. Use purchased linear guides rather than structural printed bearing parts.
3. Use laser-cut and formed metal only where it improves function, alignment, protection, or appearance.
4. Keep exterior skins removable so the machine looks finished without becoming painful to service.
5. Keep the motion frame independent from the water pan and slat loads.
6. Select standard-length motion components before freezing the frame dimensions.
7. Commission the machine in stages: motion, homing, probing, torch control, fixed-height cuts, then THC.

## Baseline control architecture

- V1 Engineering Jackpot CNC Controller V1.2.1
- ESP32 running FluidNC
- Independent Y-left and Y-right motors
- Separate Y home switches for gantry squaring
- Isolated dry-contact torch-start relay
- Floating-head or equivalent material-surface probing
- Arc OK only through a verified isolated interface
- No divided arc-voltage connection directly to Jackpot GPIO

## Reference use

The CrossFire PRO MAX guide contributes assembly sequencing, dual-Y layout, bearing adjustment concepts, water-pan construction, rail alignment, and commissioning discipline.

The JD's Garage package contributes a low-cost tube-frame approach, belt-drive examples, metal-part drawings, printable jigs/components, Z-axis examples, electronics notes, and startup files.

The X-1 Rev A plan combines those lessons with the actual project constraints. None of the references are treated as final X-1 dimensions.

## Definition of success

The X-1 is successful when it can:

- home and square repeatedly;
- move through full X/Y/Z travel without binding or lost steps;
- probe material repeatably;
- fire and extinguish the torch safely;
- cut straight lines and basic profiles at fixed height;
- produce repeatable dimensions and acceptable edge quality;
- be diagnosed and repaired without proprietary software or undocumented hardware.
