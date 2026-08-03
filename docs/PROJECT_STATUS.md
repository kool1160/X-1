# X-1 Project Status

**Status date:** 2026-08-03  
**Active phase:** Phase 1 — Precision Motion, Plasma Process, and Control Freeze  
**Project owner:** Chris Hilton  
**Primary objective:** Freeze a compact 10–18 gauge precision plasma architecture that approaches fiber-laser-like contour quality as closely as practical without fiber-laser cost.

## Current baseline

- Mission: precision mild-steel cutting from 10 gauge through 18 gauge
- Fine-detail emphasis: 14, 16, and 18 gauge intricate signs and delicate profiles
- Heavier-sheet requirement: clean, accurate, repeatable 10 and 12 gauge profiles
- Reality boundary: no claim of fiber-laser kerf, heat-affected zone, or minimum feature size
- Structure: available 1/8-inch-wall tube with laser-cut/formable metal parts
- Water bed: one-piece welded pan, designed so welding distortion does not alter rail alignment
- Guidance: profile linear rails on X and both Y sides
- Main-axis drive: recirculating ball screws on X, Y-left, and Y-right
- Main-axis ACME screws: excluded
- Tube-running rolling carriages: excluded
- Gantry: independent Y-left/Y-right drive and automatic squaring
- Z: powered precision slide with mandatory floating touch-off and separate breakaway
- Baseline plasma candidate: on-hand LOTOS APEX LTP6300DCNC with machine torch, non-HF blowback start, CNC torch input, Arc OK, and 1:1 raw arc-voltage output
- Comparison plasma source: on-hand Everlast PowerPlasma 82i with machine torch
- Production source/torch/consumables: open pending controlled 10–18 gauge cut tests
- THC: mandatory closed-loop arc-voltage THC; LOTOS raw voltage requires a properly engineered isolated high-voltage divider/THCAD interface
- Preferred control direction: LinuxCNC + QtPlasmaC with deterministic Ethernet motion and isolated arc-voltage interface
- FluidNC/Jackpot: retained only as a candidate pending documented requirement testing
- Operator interface: complete plasma-machine interface; generic G-code sender alone is not acceptable

## Process-quality rule

The machine frame is only one part of the result. X-1 shall be developed as a complete cutting system including:

- motion accuracy and reversal performance;
- source, torch, and consumable selection;
- dry and pressure-stable compressed air;
- probing, pierce height, cut height, and torch timing;
- position-aware THC and velocity anti-dive;
- CAM strategy, small-hole behavior, kerf compensation, and cut sequence;
- material-specific profiles and controlled test coupons.

## CrossFire PRO reference boundary

Keep as references:

- compact packaging;
- dual-Y layout;
- frame and water/slat concepts;
- powered floating-head purpose;
- assembly and alignment sequence.

Do not copy:

- ACME main-axis screws;
- acetal anti-backlash nuts;
- rolling bearings directly on tube rails;
- Langmuir controls, FireControl, computer, or LS-THC.

## Current active issues

1. **#3 — Select exact profile rails, blocks, lengths, and mounting strategy**
2. **#4 — Select exact ball screws, nuts, supports, couplers, motors, and drives**
3. **#5 — Inventory reusable controls, motors, drives, power supplies, plasma sources, and enclosure hardware**
4. **#8 — Select the closed-loop THC and isolated voltage architecture**
5. **#9 — Select/validate the production operator and controller software stack**
6. **#6 — Build the Rev B SolidWorks precision-machine assembly after components freeze**
7. **#15 — Select the production plasma source, machine torch, fine-cut consumables, air treatment, and 10–18 gauge cut charts**

## Immediate next actions

1. Freeze the practical material-support target and desired cut envelope.
2. Set target cut speed, rapid speed, acceleration, backlash, and repeatability requirements.
3. Select Y and X profile-rail candidates from exact drawings.
4. Build candidate ball-screw calculations for X and Y using actual bearing span, root diameter, support arrangement, RPM, torque, and inertia.
5. Compare closed-loop NEMA 23/24 drives against 400 W-class AC servos.
6. Identify the exact LOTOS machine torch and every available low-amperage nozzle/electrode/shield combination.
7. Verify the LOTOS CNC interfaces: torch-start contacts, Arc OK contact type, and loaded 1:1 raw arc-voltage behavior.
8. Bench-test both the LOTOS LTP6300DCNC and Everlast PowerPlasma 82i on controlled 10, 12, 14, 16, and 18 gauge coupons.
9. Compare the better on-hand result against at least one mechanized fine-cut plasma process before declaring the production source.
10. Select LinuxCNC/QtPlasmaC Ethernet hardware and isolated arc-voltage input, while documenting cost and availability.
11. Design the one-piece pan and rail-support structure so final rail alignment occurs after welding.
12. Design the Z floating touch-off and breakaway system.
13. Create the first precision-motion SolidWorks envelope and collision study.

## Phase 1 exit criteria

- 10–18 gauge mission and realistic laser-comparison boundary frozen;
- material support and cutting envelope frozen;
- exact X/Y profile rails and blocks selected;
- exact X/Y ball screws, nuts, supports, and couplers selected;
- critical-speed, linear-speed, torque, acceleration, and resolution calculations completed;
- motors and drives selected;
- Z guide, screw, floating mechanism, touch-off switch, and breakaway selected;
- one-piece pan/frame/rail-mount architecture frozen;
- production plasma source, torch, consumables, air-treatment requirements, and baseline cut charts selected;
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
- building an actual fiber laser source or unsafe open Class 4 laser system;
- rotary axis, nesting, quoting, cloud, mobile, AI, or commercial packaging;
- custom operator software that merely duplicates mature QtPlasmaC functions before the machine architecture is frozen.

## Update rule

Update this file whenever the active phase, immediate priority, major blocker, or architecture boundary changes. The current repository status overrides older chat summaries and superseded concepts.
