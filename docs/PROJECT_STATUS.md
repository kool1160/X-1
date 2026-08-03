# X-1 Project Status

**Status date:** 2026-08-03  
**Active phase:** Phase 1 — CrossFire PRO Mechanical Reconstruction  
**Project owner:** Chris Hilton  
**Primary objective:** Reconstruct a mechanically faithful standard CrossFire PRO frame and motion system, then operate it with Jackpot/FluidNC, X-1 Control, and X-1 THC.

## Current baseline

- Mechanical authority: standard CrossFire PRO, not PRO MAX
- Published cutting envelope: 48.25 in X × 33.3 in Y
- Published floor space: approximately 54.2 in × 69.5 in
- Frame: structural steel tube, stanchions, gussets, skirts, water tray, and slat bed patterned after PRO
- Guidance: adjustable ball-bearing carriages on zinc-plated tube rails
- X drive: 1/2-10, 5-start ACME lead screw, acetal anti-backlash nut
- Y drives: two 3/8-8, 4-start ACME lead screws, acetal anti-backlash nuts
- Main-axis advance: 0.5 inch per revolution on X and Y
- Screw support: motor coupler at drive end, 608 bearing at opposite end
- Main motors: three NEMA 23 motors, 284 oz-in equivalent
- Z: powered floating head/IHS architecture, NEMA 23, 180 oz-in equivalent
- Controller: V1 Engineering Jackpot CNC Controller V1.2.1
- Firmware: FluidNC or controlled X-1 fork
- Operator software: dedicated X-1 Windows application
- Plasma source: Everlast PowerPlasma 82i
- THC: required; X-1 implementation, not LS-THC

## Excluded Langmuir systems

- Langmuir control electronics
- FireControl
- Langmuir computer/touchscreen
- OEM wiring enclosure internals
- LS-THC and Langmuir voltage interface

## Current active issues

1. **#3 — Reconstruct CrossFire PRO tube rails and carriages**
2. **#4 — Source CrossFire PRO-equivalent ACME screws, nuts, bearings, couplers, and motors**
3. **#5 — Inventory reusable controls, motors, drives, and power supplies**
4. **#8 — Select and design the required X-1 THC architecture**
5. **#9 — Prove X-1 Control communication and state handling**

## Blocked work

- **#6 — Rev B SolidWorks and manufacturing package** is blocked by missing frame, rail, carriage, gantry, mount, water-tray, and Z manufacturing dimensions.
- **#7 — Final FluidNC configuration** is blocked by final motor assignment, I/O map, homing strategy, Z/IHS details, and THC boundary.
- Final purchase BOM is blocked by exact screw lengths, end machining, nut patterns, bearing mounts, couplers, motors, and bearings.

## Immediate next actions

1. Build the source-evidence table in `docs/CROSSFIRE_PRO_MECHANICAL_BASELINE.md`.
2. Source exact-equivalent 3/8-8 4-start and 1/2-10 5-start ACME screws and acetal anti-backlash nuts.
3. Determine exact screw lengths and turned/tapped end geometry.
4. Reconstruct the overall frame from the published footprint, cutting envelope, water-pan dimensions, guide images, and assembly relationships.
5. Reconstruct Y stanchions, tube rails, carriage weldments, bearing blocks, gantry tube, X carriage, and screw mounts.
6. Reconstruct the floating Z and IHS mechanism.
7. Mark every dimension as published, measured, derived, or inferred.
8. Create the first full SolidWorks envelope model and verify the published cutting area.
9. Integrate Jackpot/FluidNC and X-1 THC boundaries without changing the mechanical envelope unless required.

## Phase 1 exit criteria

- exact screw series, lengths, end machining, nuts, bearings, couplers, and motors selected;
- frame tube sections, cut lengths, and hole patterns reconstructed;
- rail/stanchion/carriage geometry reconstructed;
- gantry/X-carriage geometry reconstructed;
- water tray, drains, slats, and holders reconstructed;
- Z/IHS geometry reconstructed;
- SolidWorks assembly reproduces 48.25 in × 33.3 in cutting envelope and approximately 54.2 in × 69.5 in floor space;
- every critical dimension has evidence classification;
- decision log and requirements are current;
- no unlabeled inferred geometry remains in released manufacturing drawings.

## Current exclusions

Do not expand active work into:

- PRO MAX geometry or 4 × 4 expansion;
- profile linear rails or ball screws unless the replica architecture fails a documented requirement;
- Mesa/LinuxCNC/EtherCAT migration without a documented FluidNC failure;
- fiber laser, rotary axis, nesting, quoting, cloud, mobile, AI, or commercial packaging;
- cosmetic redesign before the mechanical clone is dimensionally closed.

## Update rule

Update this file whenever the active phase, immediate priority, major blocker, or replica boundary changes. The current repository status overrides older chat summaries and superseded concepts.
