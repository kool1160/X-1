# X-1 Project Status

**Status date:** 2026-08-04  
**Active phase:** Phase 0 — Compare SPX4300 Retrofit vs New Compact Machine  
**Project owner:** Chris Hilton  
**Lock state:** No mechanical, drive, control, or machine-path decision is locked unless Chris explicitly says to lock it.

## Active planning question

Which investment produces the best precision-plasma result:

1. upgrade the existing large SPX4300-based table;
2. build a separate compact X-1 machine;
3. use a staged approach where selected retrofit work proves the source, controls, THC, and motion concepts before a final path is chosen?

## Shared performance objective

- Precision cutting in 10, 12, 14, 16, and 18 gauge mild steel.
- Highest detail priority on 14–18 gauge signs and small features.
- Clean, accurate, repeatable profiles on 10–12 gauge.
- Improve motion, torch height, consumables, air, CAM, and controls until the plasma process is the dominant remaining limitation.
- No claim that conventional plasma will equal fiber-laser kerf or minimum feature size.

## Option A — SPX4300 precision retrofit

Provisional study only.

Potentially retain:

- main frame;
- water pan and slat bed;
- legs and supports;
- source and machine torch;
- enclosure shell and portions of cable routing.

Potentially replace or redesign:

- tube-running bearings and carriages;
- X and Y guidance;
- rack, pinions, preload, or reduction;
- open-loop motors and drives;
- gantry if weight or deflection is excessive;
- Z slide, touch-off, and breakaway;
- controller, operator interface, and THC.

The long Y axes make precision rack drive a leading provisional option. Conventional rotating ball screws are not assumed appropriate for 8–10 foot travel.

## Option B — New compact X-1

Provisional study only.

Potential advantages:

- lower moving mass;
- shorter rails and drives;
- higher acceleration for intricate profiles;
- easier contamination protection and alignment;
- no downtime or risk to the existing production table.

Potential disadvantages:

- duplicated frame, pan, electrical system, and floor space;
- additional cost for a complete second machine;
- smaller work envelope.

## On-hand plasma process candidates

- LOTOS LTP5500DCNC with PlasmaDyn iPT60/PTM-60 machine torch;
- Everlast PowerPlasma 82i with machine torch.

Both remain test candidates. Neither is owner-locked as the final production source.

## Current controls candidates

- LinuxCNC + QtPlasmaC with deterministic Ethernet hardware;
- Jackpot + FluidNC if it proves the complete plasma workflow;
- other systems that satisfy the same motion, probing, recovery, operator-interface, and position-aware THC requirements.

No control platform is locked.

## Immediate next actions

1. Inspect and measure the existing SPX4300 table:
   - table size and actual cut envelope;
   - frame diagonals and twist;
   - Y rail straightness and parallelism;
   - gantry weight and deflection;
   - carriage play;
   - rack backlash and pinion engagement;
   - current motor, drive, and power-supply details.
2. Record the current full-speed motion and cut problems.
3. Create a Level 1, Level 2, and Level 3 retrofit cost and downtime estimate.
4. Create an equivalent compact-machine cost estimate using the same source, control, THC, and quality targets.
5. Test the LOTOS/iPT60 and Everlast source packages on controlled 10–18 gauge coupons.
6. Select nothing for purchase until the retrofit-versus-new-build comparison is reviewed by the project owner.

## Active documents

- `docs/SPX4300_RETROFIT_EVALUATION.md`
- `docs/PROJECT_RULES.md`
- `docs/PLASMA_SOURCE_BASELINE.md`
- `docs/CUT_QUALITY_TARGETS.md`
- supplied SPX4300 frame and gantry assembly guides

## Exit criteria for this phase

- existing table measurements recorded;
- retrofit levels defined with component categories, risk, downtime, and cost;
- compact-machine alternative defined at the same level;
- source/torch test plan defined;
- control and THC candidates compared without assumption;
- project owner chooses the next direction or keeps the comparison open;
- only decisions explicitly approved with the word `lock` are entered as locked.
