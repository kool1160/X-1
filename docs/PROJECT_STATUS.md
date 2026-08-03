# X-1 Project Status

**Status date:** 2026-08-02  
**Active phase:** Phase 1 — Architecture and Component Freeze  
**Project owner:** Chris Hilton  
**Primary objective:** Freeze a buildable, affordable compact half-sheet X-1 architecture without drifting into unnecessary machine length or unrelated platforms.

## Current baseline

- Project name: X-1 — Laser X Design 1
- Machine type: CNC plasma table
- Sheet-support area: approximately 50 × 50 inches clear, allowing a 48 × 48 inch half-sheet to load with about 1 inch clearance on every side
- Cutting envelope: open and expected to be smaller than the support area; finalized from actual carriage, guide, screw, torch-offset, limit, and overtravel geometry
- Extra length: not required; the existing large laser handles long work
- Frame: welded 1/8-inch-wall steel tube
- Guides: purchased linear guides with metal carriages
- Main-axis drive: ball screws selected for X, Y-left, and Y-right
- Main-axis screw diameter baseline: 16 mm nominal, approximately 5/8 inch
- Gantry: independent Y-left and Y-right drives with automatic squaring
- Controller: V1 Engineering Jackpot CNC Controller V1.2.1
- Firmware: FluidNC
- Operator interface: dedicated X-1 Windows machine software
- Plasma source: Everlast PowerPlasma 82i
- THC: required; architecture open and active

## Current active issues

1. **#5 — Inventory on-hand controls, motors, drives, and power supplies**
2. **#3 — Select X and Y linear guides and standard lengths**
3. **#4 — Choose actual ball-screw components and verify usable travel/speed**
4. **#8 — Select and design the required THC architecture**
5. **#9 — Build dedicated X-1 operator software**

Issue #9 is limited during this phase to communication proof, state handling, architecture, and requirements. Full application development waits for machine signals and operating sequences to be frozen.

## Blocked work

- **#6 — Rev B SolidWorks assembly and manufacturing package** is blocked by guide, screw package, motor/driver, Z, travel, and THC-interface selections.
- **#7 — Final FluidNC configuration** is blocked by motor/driver selection, travel, pin mapping, switch arrangement, and selected THC boundary.
- Final BOM and purchase package are blocked by exact component selection.
- Released wiring diagrams are blocked by the final I/O map and plasma/THC architecture.

## Immediate next actions

1. Photograph and identify all reusable motion and control hardware.
2. Collect exact listings and drawings for guide candidates sized around the approximately 50 × 50 inch support bed.
3. Collect exact listings and drawings for 16 mm ball-screw packages.
4. Compare likely screw lengths around 1400–1500 mm and calculate actual usable stroke from end machining, bearing supports, nut length, coupler, and limit allowance.
5. Compare 1605 and 1610 or other available leads using actual root diameter, bearing span, critical-speed limit, desired cutting speed, and desired rapid speed.
6. Calculate complete delivered cost for two Y screws and one X screw; treat Z separately.
7. Document the installed Jackpot and FluidNC versions and available I/O.
8. Evaluate the viable THC paths in `THC_ARCHITECTURE.md` and select one.
9. Prove basic FluidNC communication from the future X-1 operator software stack.

## Phase 1 exit criteria

Phase 1 is complete only when all of the following are true:

- exact X and Y guide packages selected;
- exact X, Y-left, and Y-right ball-screw packages selected;
- exact Z guide and drive selected;
- motors and driver strategy selected;
- the table provides approximately 50 × 50 inches of clear sheet-support area;
- usable X/Y/Z travel calculated and the final compact cut envelope frozen;
- ball-screw critical speed and target cut/rapid speeds verified;
- Jackpot and FluidNC I/O requirements verified;
- required THC architecture selected with defined hardware and firmware boundaries;
- X-1 operator-software communication path proven;
- selected components have verified drawings or physical measurements;
- decision log and requirements updated;
- no dimension-critical or control-critical `TBD` blocks the Rev B assembly.

## Current exclusions

Do not expand active work into:

- fiber lasers;
- Mesa/LinuxCNC/EtherCAT migration without a documented FluidNC failure;
- rotary axes;
- 4 × 5, 4 × 6, or 4 × 8 expansion outside the locked compact half-sheet requirement;
- nesting, quoting, cloud, mobile, AI, or commercial-product features;
- cosmetic detail design before the core machine envelope and guards are established.

Record those ideas in `PARKING_LOT.md` and return to the active issue.

## Update rule

Update this file whenever the active phase, immediate priority, major blocker, or phase gate changes. Do not use old chat summaries as the project baseline when this file has newer information.
