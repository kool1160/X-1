# X-1 Development Plan

## Phase 0 — Reference, requirements, and project control

- Preserve original reference files.
- Separate source-derived observations from X-1 engineering decisions.
- Establish the project summary, status, requirements, decision log, rules, architecture, parking lot, and GitHub workflow.
- Do not release manufacturing drawings from nominal online dimensions.

**Exit condition:** sources of truth exist and the active phase is explicit.

## Phase 1 — Architecture and component freeze

Select actual purchasable components for:

- Y guides and blocks;
- X guides and blocks;
- X/Y drive system;
- motors and drivers;
- Z guide and drive;
- cable chain;
- home/probe switches;
- torch relay and Arc OK isolation;
- isolated arc-voltage measurement;
- complete FluidNC-compatible THC architecture.

Also:

- inventory reusable hardware;
- calculate usable travel from exact component geometry;
- verify the installed Jackpot and FluidNC versions and available I/O;
- prove basic FluidNC communications for X-1 Control;
- define controller, THC, and operator-software subsystem boundaries.

Record delivered cost, exact dimensions, listing/model, replacement availability, datasheets, measurements, assumptions, and risks.

**Exit condition:** every dimension-critical component has an exact model and drawing or verified measurement; the THC architecture has a proven position-aware control concept and selected interface direction; X-1 Control can communicate with the controller.

## Phase 2 — Rev B engineering release

Create:

- complete SolidWorks assembly;
- final work envelope and overall size;
- tube cut list;
- Y truck and gantry end-plate drawings;
- X carriage and Z drawings;
- motor, nut, rack, pulley, bearing, or end-support mounts;
- rail drilling/slot tables;
- water-pan and slat drawings;
- removable skirt and guard envelopes;
- released BOM;
- preliminary wiring and terminal diagrams;
- FluidNC I/O map and configuration skeleton;
- THC signal/control diagram and bench hardware design;
- X-1 Control communication specification and machine-state model.

**Exit condition:** no critical hole pattern is based on a generic product picture and no control-critical signal path is undefined.

## Phase 3 — Frame and pan fabrication

1. Cut and deburr tube.
2. Fixture and tack the main frame.
3. Equalize diagonals and control twist.
4. Weld with a balanced sequence.
5. Allow full cooling and remeasure.
6. Add adjustable/bolt-on rail mounting surfaces.
7. Fabricate the separate pan/slat support system.
8. Fabricate removable water pan, drains, slat combs, and slats.

**Hold point HP-1:** frame has no rock, diagonals and twist are documented, and rail pads can be aligned straight.

## Phase 4 — Mechanical motion assembly

1. Establish one Y rail as the master.
2. Install both Y trucks.
3. Float and align the second Y rail by moving the gantry through full travel.
4. Build and install the gantry without forcing the trucks out of alignment.
5. Install X guide(s), drive, carriage, and cable chain.
6. Install Z guide, drive, probe mechanism, and torch mount.
7. Add hard stops and removable rail/drive guards.

**Hold point HP-2:** X/Y/Z move through full travel with consistent force and no truck rocking, screw/rack/belt binding, or guard interference.

## Phase 5 — Electrical and THC bench build

- Build the enclosure with separated power, motor, controller, plasma-interface, and field-terminal zones.
- Power and test the Jackpot without the plasma cutter connected.
- Test each motor channel individually.
- Test every switch and E-stop status input by hand.
- Test the torch relay as dry contacts only.
- Verify power-supply polarity, voltage, driver current, grounding, and cable shielding.
- Build the selected isolated Arc OK and voltage-measurement interface.
- Test the voltage interface with a safe low-voltage simulator.
- Prove scaling, signal loss, overrange, filtering, status reporting, and fault behavior.
- Bench-test position-aware THC Z correction during simultaneous X/Y motion.

**Hold point HP-3:** E-stop removes motion/torch capability, every I/O point is documented, the voltage input is isolated, and simulated THC correction cannot lose Z position.

## Phase 6 — FluidNC and X-1 Control commissioning

- Create and commit the first machine configuration.
- Verify axis directions at low current and speed.
- Home X, Z, Y-left, and Y-right.
- Verify repeatable gantry squaring.
- Calibrate commanded travel against measured travel.
- Tune conservative velocity and acceleration.
- Run dry G-code over the full work envelope.
- Connect X-1 Control through the approved transport.
- Verify machine state, coordinates, jogging, hold, resume, reset, alarms, and logs.
- Run simulated THC status and command workflows through X-1 Control.

**Hold point HP-4:** repeated power cycles and homing produce stable square and position; X-1 Control can perform the basic machine workflow without a generic sender.

## Phase 7 — Live plasma baseline

1. Connect isolated torch start.
2. Verify torch ON/OFF with motion disabled.
3. Verify Arc OK through the proven isolated interface.
4. Verify the divided-voltage interface does not alter the Everlast output.
5. Establish probing and pierce-height behavior.
6. Cut fixed-height straight lines.
7. Cut squares and circles.
8. Separate CAM lead-in/lead-out problems from machine-control problems.
9. Record consumables, amperage, air pressure, feed, pierce delay, physical voltage, and results.

**Hold point HP-5:** basic profiles cut reliably at fixed height, Arc OK and voltage are stable, and the plasma interface produces no unexplained controller behavior.

## Phase 8 — Live THC integration and validation

- Enable THC only on conservative straight test cuts.
- Verify correction direction, deadband, rate limits, target voltage, delay, and Z tracking.
- Tune on controlled slope and warped sheet.
- Validate velocity/corner anti-dive.
- Validate holes, lead-ins, lead-outs, kerf crossings, and end-of-cut behavior.
- Test Arc OK loss, cut loss, sensor loss, implausible voltage, hold, resume, reset, E-stop, and controller restart.
- Log voltage, feed rate, Z correction, active state, faults, and resulting cut height.
- Expose validated controls and diagnostics in X-1 Control.

**Hold point HP-6:** THC maintains usable cut height over representative warped material without torch dive, accumulated Z-position error, motion corruption, or unsafe fault behavior.

## Phase 9 — Production operator workflow

- Complete G-code validation and visualization.
- Implement material profiles and THC settings.
- Implement perimeter trace and torch-inhibited dry run.
- Implement stored-job upload/start, progress, pause, resume, stop, and recovery.
- Implement diagnostics, configuration backup, event logs, and maintenance records.
- Validate the complete workflow without the stock WebUI, generic sender, or terminal.

**Hold point HP-7:** an operator can prepare, verify, run, pause, recover, and diagnose a normal plasma job entirely through X-1 Control.

## Phase 10 — Finish and as-built release

- Fit cosmetic skirts and branded panels.
- Complete guards and service labels.
- Update as-built CAD, BOM, wiring, configuration, software, and THC documentation.
- Publish Rev C as-built documents.
- Archive known-good FluidNC/X-1 firmware, X-1 Control release, calibration, and test records.

**Exit condition:** X-1 meets all locked requirements and has a complete reproducible as-built package.
