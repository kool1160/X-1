# X-1 Project Status

**Status date:** 2026-08-02  
**Active phase:** Phase 1 — Architecture and Component Freeze  
**Project owner:** Chris Hilton  
**Primary objective:** Freeze a buildable, affordable X-1 architecture without drifting into unrelated machine platforms or premature detail design.

## Current baseline

- Project name: X-1 — Laser X Design 1
- Machine type: CNC plasma table
- Material width: at least 48 inches
- Target Y cutting travel: approximately 60–72 inches, based on selected standard components
- Frame: welded 1/8-inch-wall steel tube
- Guides: purchased linear guides with metal carriages
- Drive: open decision among rack and pinion, timing belt, and ball screw
- Gantry: independent Y-left and Y-right drives with automatic squaring
- Controller: V1 Engineering Jackpot CNC Controller V1.2.1
- Firmware: FluidNC
- Operator interface: dedicated X-1 Windows machine software
- Plasma source: Everlast PowerPlasma 82i
- THC: required; architecture open and active

## Current active issues

1. **#5 — Inventory on-hand controls, motors, drives, and power supplies**
2. **#3 — Select X and Y linear guides and standard lengths**
3. **#4 — Choose X/Y drive architecture and actual components**
4. **#8 — Select and design the required THC architecture**
5. **#9 — Build dedicated X-1 operator software**

Issue #9 is limited during this phase to communication proof, state handling, architecture, and requirements. Full application development waits for machine signals and operating sequences to be frozen.

## Blocked work

- **#6 — Rev B SolidWorks assembly and manufacturing package** is blocked by guide, drive, motor/driver, Z, travel, and THC-interface selections.
- **#7 — Final FluidNC configuration** is blocked by motor/driver selection, travel, pin mapping, switch arrangement, and selected THC boundary.
- Final BOM and purchase package are blocked by exact component selection.
- Released wiring diagrams are blocked by the final I/O map and plasma/THC architecture.

## Immediate next actions

1. Photograph and identify all reusable motion and control hardware.
2. Collect exact listings and drawings for serious guide candidates.
3. Collect exact listings and drawings for serious rack, belt, and screw candidates.
4. Calculate usable travel and complete delivered cost for each drive package.
5. Document the installed Jackpot and FluidNC versions and available I/O.
6. Evaluate the three viable THC paths in `THC_ARCHITECTURE.md` and select one.
7. Prove basic FluidNC communication from the future X-1 operator software stack.

## Phase 1 exit criteria

Phase 1 is complete only when all of the following are true:

- exact X and Y guide packages selected;
- exact X/Y drive components selected;
- exact Z guide and drive selected;
- motors and driver strategy selected;
- usable X/Y/Z travel calculated;
- final target work envelope frozen;
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
- 4×8 expansion outside the selected component tier;
- nesting, quoting, cloud, mobile, AI, or commercial-product features;
- cosmetic detail design before the core machine envelope and guards are established.

Record those ideas in `PARKING_LOT.md` and return to the active issue.

## Update rule

Update this file whenever the active phase, immediate priority, major blocker, or phase gate changes. Do not use old chat summaries as the project baseline when this file has newer information.
