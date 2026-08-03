# X-1 Project Status

**Status date:** 2026-08-03  
**Active phase:** Phase 1 — Precision Motion and Plasma Architecture Freeze  
**Project owner:** Chris Hilton  
**Primary objective:** Freeze a compact precision-sign-cutter architecture for intricate 16-gauge and 18-gauge work without drifting back into a low-cost CrossFire clone or duplicating the existing large plasma table.

## Current baseline

- Mission: intricate signs, delicate profiles, small holes/arcs, and repeatable thin-sheet cutting
- Structure: available 1/8-inch-wall tube with laser-cut/formable metal parts
- Water bed: one-piece welded pan, designed so welding distortion does not alter rail alignment
- Guidance: profile linear rails on X and both Y sides
- Main-axis drive: recirculating ball screws on X, Y-left, and Y-right
- Main-axis ACME screws: excluded
- Tube-running rolling carriages: excluded
- Gantry: independent Y-left/Y-right drive and automatic squaring
- Z: powered precision slide with mandatory floating touch-off and separate breakaway
- Plasma source: Everlast PowerPlasma 82i
- THC: mandatory closed-loop arc-voltage THC
- Preferred control direction: LinuxCNC + QtPlasmaC with deterministic Ethernet motion and isolated arc-voltage interface
- FluidNC/Jackpot: retained only as a candidate pending documented requirement testing
- Operator interface: complete plasma-machine interface; generic G-code sender alone is not acceptable

## CrossFire PRO reference boundary

Keep as references:

- compact table proportions and packaging;
- dual-Y layout;
- frame/leg/stanchion concepts;
- one-piece water-bed adaptation;
- slat system;
- powered floating-head purpose;
- assembly and alignment sequence.

Do not copy:

- ACME main-axis screws;
- acetal anti-backlash nuts;
- rolling bearings directly on tube rails;
- Langmuir controls, FireControl, computer, or LS-THC.

The assembly guide confirms the reference machine uses three lead screws, rolling tube carriages, NEMA 23 motors, and a floating IHS head. Those features explain the reference architecture but are not all suitable for the X-1 precision target.

## Current active issues

1. **#3 — Select exact profile rails, blocks, lengths, and mounting strategy**
2. **#4 — Select exact ball screws, nuts, supports, couplers, motors, and drives**
3. **#5 — Inventory reusable controls, motors, drives, power supplies, and enclosure hardware**
4. **#8 — Select the closed-loop THC and isolated voltage architecture**
5. **#9 — Select/validate the production operator and controller software stack**
6. **#6 — Build the Rev B SolidWorks precision-machine assembly after components freeze**

## Immediate next actions

1. Freeze the practical material-support target and desired cut envelope.
2. Set target thin-sheet cut speed, rapid speed, acceleration, and contouring requirements.
3. Select Y profile-rail candidates and X profile-rail candidates from exact drawings.
4. Build candidate ball-screw calculations for:
   - X: 16 mm and 20 mm diameter; 10 mm and higher leads;
   - Y-left/Y-right: 16 mm and 20 mm diameter; 10 mm and higher leads;
   - fixed-supported and fixed-fixed support arrangements.
5. Calculate actual bearing span, root diameter, 80%-critical-speed operating ceiling, maximum linear speed, motor RPM, torque, and screw inertia.
6. Compare closed-loop NEMA 23/24 drives against 400 W-class AC servos.
7. Select LinuxCNC/QtPlasmaC Ethernet hardware and isolated arc-voltage input, while documenting the cost and availability.
8. Design the one-piece pan and rail-support structure so final rail alignment happens after welding.
9. Design the Z floating touch-off and breakaway system.
10. Create the first precision-motion SolidWorks envelope and collision study.

## Phase 1 exit criteria

- machine mission and material/cut envelope frozen;
- exact X/Y profile rails and blocks selected;
- exact X/Y ball screws, nuts, supports, and couplers selected;
- critical-speed, linear-speed, torque, acceleration, and resolution calculations completed;
- motors and drives selected;
- Z guide, screw, floating mechanism, touch-off switch, and breakaway selected;
- one-piece pan/frame/rail-mount architecture frozen;
- controller, operator interface, I/O, Arc OK, voltage input, and THC architecture selected;
- selected components have verified drawings or physical measurements;
- decision log and requirements current;
- Rev B assembly can be modeled without dimension-critical or control-critical guesses.

## Current exclusions

Do not expand active work into:

- an exact CrossFire PRO replica;
- ACME or trapezoidal main-axis screws;
- tube-running rolling carriages;
- 4 × 8 expansion or attempts to replace the existing large plasma table;
- fiber laser, rotary axis, nesting, quoting, cloud, mobile, AI, or commercial packaging;
- custom operator software that merely duplicates mature QtPlasmaC functions before the machine architecture is frozen.

## Update rule

Update this file whenever the active phase, immediate priority, major blocker, or architecture boundary changes. The current repository status overrides older chat summaries and superseded concepts.
