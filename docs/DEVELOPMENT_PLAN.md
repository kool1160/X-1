# X-1 Development Plan

## Phase 0 — Reference, requirements, and project control

- Preserve original reference files.
- Separate source-derived observations from X-1 engineering decisions.
- Establish project summary, status, requirements, decisions, rules, architecture, and GitHub workflow.
- Do not release manufacturing drawings from unverified image estimates.

**Exit condition:** project authority and active scope are explicit.

## Phase 1 — CrossFire PRO mechanical reconstruction

Reconstruct and verify:

- lower frame tubes, legs, cross tubes, lower rails, stanchions, gussets, and skirts;
- Y zinc-plated tube rails and fixed/adjustable bearing carriages;
- gantry tube and rolling X carriage;
- 3/8-8 4-start Y screws and 1/2-10 5-start X screw;
- anti-backlash nuts, 608 bearings, couplers, and NEMA 23 motors;
- motor mounts, bearing mounts, and floating lead-nut mounts;
- two-piece water tray, drains, slat holders, and slats;
- powered floating Z, torch mount, IHS switch, and Z drive.

For every critical dimension, record whether it is Published, Measured, Derived, or Inferred.

**Exit condition:** a closed SolidWorks assembly reproduces the published 48.25 × 33.3 in cutting envelope and approximately 54.2 × 69.5 in floor space, with no inferred critical geometry in released drawings.

## Phase 2 — Mechanical Rev B release

Create:

- complete SolidWorks assembly;
- tube cut list and drilling tables;
- stanchion, carriage, bearing-block, gantry, X-carriage, motor-mount, bearing-mount, and lead-nut drawings;
- ACME screw machining drawings;
- Z/IHS drawings;
- water-tray, drain, slat-holder, slat, skirt, and gusset drawings;
- released DXFs and PDFs;
- mechanical BOM and supplier records;
- alignment and assembly checklist modeled on the CrossFire PRO guide.

**Exit condition:** the complete mechanical table can be fabricated and assembled without guessing a critical dimension.

## Phase 3 — Frame, tray, and motion fabrication

1. Cut and deburr tube and plate parts.
2. Fixture and assemble the lower frame.
3. Square lower rails to cross tubes and hold rail spacing within the verified tolerance.
4. Install stanchions and Y tube rails.
5. Assemble fixed/adjustable rolling-bearing carriages.
6. Assemble gantry and X carriage.
7. Install water tray, drains, slat holders, and slats.
8. Install motor mounts, bearing mounts, lead nuts, screws, couplers, and motors.
9. Assemble and tram powered floating Z/IHS.
10. Cycle full travel and verify published work envelope.

**Hold point HP-1:** frame is square, Y rails are parallel within 1/32 in, bearings are preloaded without binding, and all axes move freely.

## Phase 4 — Jackpot/FluidNC electrical bench build

- Build an X-1 enclosure independent of Langmuir electronics.
- Test Jackpot, supplies, motors, switches, and E-stop with plasma disconnected.
- Configure X, Y-left, Y-right, and Z channels.
- Verify screw calibration using 0.5 in/rev main-axis advance.
- Establish repeatable squaring and IHS behavior.
- Build isolated torch-start and Arc OK interfaces.

**Hold point HP-2:** hardware safety works, every I/O point is documented, and the mechanical replica moves repeatably under FluidNC.

## Phase 5 — THC bench development

- Verify Everlast divider pins, polarity, ratios, loaded behavior, and meter-loading anomaly.
- Build isolated voltage measurement.
- Test with a safe low-voltage simulator.
- Prove position-aware THC Z correction during simultaneous X/Y motion.
- Define anti-dive, rate limits, target voltage, deadband, faults, and recovery.

**Hold point HP-3:** simulated THC cannot lose Z position or bypass hardware safety.

## Phase 6 — X-1 Control commissioning

- Prove USB and network communication.
- Verify machine state, coordinates, jogging, homing/squaring, hold, resume, reset, alarms, and logs.
- Add job import, preview, validation, bounds checks, trace, dry run, and stored-file execution.
- Add plasma workflow and THC status/control.

**Hold point HP-4:** normal operation no longer depends on FireControl, the stock WebUI, or a generic sender.

## Phase 7 — Live plasma baseline

1. Connect isolated torch start and Arc OK.
2. Validate IHS, pierce height, cut height, and fixed-height cuts.
3. Verify divided voltage without altering the plasma output.
4. Record cut parameters, physical voltage, and results.

**Hold point HP-5:** fixed-height cuts are repeatable and plasma signals are stable.

## Phase 8 — Live THC validation

- Enable conservative straight-line correction.
- Tune target voltage, delay, deadband, and rate limits.
- Validate warped sheet, corners, holes, lead-ins/outs, kerf crossings, and cut loss.
- Test hold, resume, reset, E-stop, Arc OK loss, sensor loss, and restart.

**Hold point HP-6:** THC maintains cut height without torch dive or accumulated Z error.

## Phase 9 — Finish and as-built release

- Add X-1 skins, guards, labels, and service access.
- Update as-built CAD, BOM, wiring, FluidNC, software, and THC documentation.
- Publish final released package and known-good configurations.

**Exit condition:** X-1 reproduces the CrossFire PRO mechanical capability while operating entirely on X-1 controls and software.
