# X-1 Project Brief

## Mission

Design and build a low-cost, serviceable CNC plasma table that uses Chris Hilton's available steel and fabrication resources while avoiding the proprietary-controller, weak diagnostics, and outdated software problems of the current MyPlasm system.

## Machine identity

- **Project:** X-1
- **Meaning:** Laser X Design 1
- **Machine type:** CNC plasma cutting table
- **Primary use:** signs, sheet-metal profiles, fabrication parts, and prototype work
- **Nominal width:** at least 48-inch cutting capacity
- **Nominal length:** component-driven; target approximately 60–72 inches

## Build philosophy

1. Use free 1/8-inch-wall tube for the structural frame.
2. Use purchased linear guides and metal structural carriages rather than structural printed bearing parts.
3. Use laser-cut and formed metal only where it improves function, alignment, protection, or appearance.
4. Keep exterior skins removable so the machine looks finished without becoming painful to service.
5. Keep the motion frame independent from the water pan and slat loads.
6. Select standard-length motion components before freezing frame dimensions.
7. Keep guides and drive systems as separate engineering decisions.
8. Use the existing Jackpot with FluidNC unless it fails a documented requirement.
9. Run the machine through dedicated X-1 operator software, not merely a generic G-code sender.
10. Commission in stages, but require automatic closed-loop THC before the machine is considered complete.

## Baseline control architecture

- V1 Engineering Jackpot CNC Controller V1.2.1
- ESP32 running FluidNC or a controlled X-1 FluidNC fork
- Independent Y-left and Y-right motors
- Separate Y home switches for gantry squaring
- Isolated dry-contact torch-start relay
- Floating-head or equivalent material-surface probing
- Arc OK only through a verified isolated interface
- Isolated and protected arc-voltage measurement
- Position-aware automatic Z correction with anti-dive and fault handling
- Dedicated Windows X-1 Control application for the machine, job, plasma, THC, diagnostic, and recovery workflow
- No divided arc-voltage connection directly to Jackpot/ESP32 GPIO

## Reference use

The CrossFire PRO MAX guide contributes assembly sequencing, dual-Y layout, bearing adjustment concepts, water-pan construction, rail alignment, and commissioning discipline.

The JD's Garage package contributes a low-cost tube-frame approach, belt-drive examples, metal-part drawings, printable jigs/components, Z-axis examples, electronics notes, and startup files.

The X-1 Rev A plan combines those lessons with the actual project constraints. None of the references are treated as final X-1 dimensions or control architecture.

## Definition of success

X-1 is successful when it can:

- home and square repeatedly;
- move through full X/Y/Z travel without binding or lost position;
- probe material repeatably;
- fire and extinguish the torch safely through verified isolation;
- cut straight lines and basic profiles at fixed height as a commissioning baseline;
- automatically maintain usable torch height over representative warped material without diving or losing Z position;
- provide live Arc OK, voltage, THC, machine, and fault diagnostics;
- run normal jobs through dedicated X-1 Control without a generic sender or terminal;
- produce repeatable dimensions and acceptable edge quality;
- be diagnosed, backed up, repaired, and reproduced without proprietary software or undocumented hardware.
