# X-1 Project Summary

## Project

**X-1 — Laser X Design 1** is a mechanically faithful CrossFire PRO-style CNC plasma table using the original machine's frame, rail, carriage, lead-screw, motor, water-table, slat-bed, and floating-Z architecture.

X-1 will **not** use Langmuir electronics, FireControl, the Langmuir computer, or the LS-THC system. The control stack remains:

- V1 Engineering Jackpot controller
- FluidNC or a controlled X-1 FluidNC fork
- dedicated X-1 Windows operator software
- X-1 isolated plasma interface and required automatic THC

## Mechanical baseline

The target mechanical envelope is the standard CrossFire PRO, not the PRO MAX:

- published cutting envelope: **48.25 in X × 33.3 in Y**
- published floor space: approximately **54.2 in × 69.5 in**
- full 4-foot sheet-width support/pass-through capability
- welded/bolted structural steel tube frame with gussets
- stainless water tray and replaceable slat bed
- zinc-plated steel tube motion rails with adjustable ball-bearing carriages
- powered floating Z axis with initial-height sensing

## Main-axis drive system

The CrossFire PRO does not use ball screws. It uses multi-start ACME lead screws with acetal anti-backlash nuts:

- **Y-left:** 3/8-8, 4-start ACME lead screw
- **Y-right:** 3/8-8, 4-start ACME lead screw
- **X:** 1/2-10, 5-start ACME lead screw
- both screw types advance **0.5 inch per revolution**
- each screw is coupled to a NEMA 23 stepper at one end and supported by a 608 bearing at the opposite end

Published motor sizes:

- X: NEMA 23, 284 oz-in
- Y-left: NEMA 23, 284 oz-in
- Y-right: NEMA 23, 284 oz-in
- Z: NEMA 23, 180 oz-in

## Replica scope

### Copy mechanically

- overall frame layout and proportions
- lower frame tubes, legs, stanchions, gussets, and skirts
- two Y tube rails and adjustable rolling carriages
- gantry tube, X carriage, motor mounts, and bearing mounts
- OEM-equivalent ACME screws, anti-backlash nuts, bearings, couplers, and NEMA 23 motors
- water tray, drains, slat holders, and slats
- powered floating Z and initial-height-sense mechanism
- assembly and alignment sequence from the CrossFire PRO guide

### Replace with X-1 systems

- motion-control electronics
- USB controller
- FireControl software
- Langmuir computer/touchscreen
- torch-firing interface
- LS-THC and voltage interface
- wiring harness and enclosure layout where needed for Jackpot/FluidNC

## Accuracy rule

The assembly guide identifies parts, hardware, sequence, screw diameters, bearings, and adjustment methods, but it is not a manufacturing drawing package. Published overall dimensions and motion specifications are authoritative; hidden hole locations, tube cut lengths, carriage plates, mount geometry, and Z details must be reconstructed from verified measurements, additional drawings, or a controlled reverse-engineering model.

The project may be called an exact mechanical replica only after the released CAD matches all verified dimensions and reproduces the published work envelope without invented critical geometry.

## Active phase

**Phase 1 — CrossFire PRO Mechanical Reconstruction**

Immediate work:

1. Build the source-derived mechanical baseline.
2. Source exact-equivalent ACME screws, nuts, bearings, couplers, and motors.
3. Reconstruct frame, rail, carriage, gantry, water tray, and Z geometry.
4. Separate verified dimensions from inferred dimensions.
5. Release a complete SolidWorks assembly, tube cut list, plate DXFs, fabrication drawings, and mechanical BOM.
6. Integrate Jackpot/FluidNC, X-1 Control, and X-1 THC without changing the mechanical envelope unless a documented interference requires it.

## Sources of truth

Read in this order:

1. [`docs/PROJECT_STATUS.md`](docs/PROJECT_STATUS.md)
2. [`docs/DECISION_LOG.md`](docs/DECISION_LOG.md)
3. [`docs/REQUIREMENTS.md`](docs/REQUIREMENTS.md)
4. [`docs/CROSSFIRE_PRO_MECHANICAL_BASELINE.md`](docs/CROSSFIRE_PRO_MECHANICAL_BASELINE.md)
5. [`docs/PROJECT_RULES.md`](docs/PROJECT_RULES.md)
6. [`docs/THC_ARCHITECTURE.md`](docs/THC_ARCHITECTURE.md)
7. [`docs/OPERATOR_SOFTWARE.md`](docs/OPERATOR_SOFTWARE.md)
8. original reference material
