# X-1 Project Rules

These rules exist to prevent scope drift, invented dimensions, duplicated work, and premature purchases or fabrication.

## 0. Project-owner lock authority

Nothing is locked unless Chris explicitly says **"lock"**, **"lock it"**, or an equally direct instruction that a named decision is now locked.

The following do **not** create a lock by themselves:

- brainstorming;
- agreeing that an option sounds good;
- calling something a baseline, favorite, recommendation, or current direction;
- merging a pull request;
- adding a requirement, issue, drawing, BOM item, or concept to the repository;
- the assistant saying that something is locked.

Until Chris explicitly locks a named decision, it remains **provisional** and may be compared, changed, removed, or replaced without a formal change-control process.

All older decision-log entries marked locked but lacking explicit project-owner authorization are considered **provisional historical directions**. They do not bind the project.

When Chris explicitly locks a decision, the repository record must include:

1. the exact decision being locked;
2. the date;
3. the project-owner authorization or a faithful summary of it;
4. the affected requirements, architecture, BOM, CAD, software, and testing documents.

## 1. One active planning question

Only work listed in `PROJECT_STATUS.md` is active.

Ideas outside the active question go in `PARKING_LOT.md`. They are not purchased, fabricated, coded, or released unless the project owner makes them active.

## 2. Authority order

When documents disagree, use this order:

1. the project owner's latest explicit instruction;
2. `PROJECT_STATUS.md` for the active planning question and current work;
3. explicitly owner-locked entries in `DECISION_LOG.md`;
4. `REQUIREMENTS.md` for provisional design targets;
5. `PROJECT_RULES.md` for process control;
6. subsystem studies, calculations, CAD, BOMs, and test records;
7. third-party references for ideas and evidence only.

A GitHub merge never overrides a later project-owner instruction.

## 3. Separate facts, assumptions, and proposals

- Mark every unverified dimension as `TBD`, `ASSUMPTION`, `DERIVED`, or `REFERENCE ONLY`.
- Do not release a mounting pattern from a seller photograph or generic family dimension.
- Use verified manufacturer drawings or measurements from the actual component.
- Calculations must state their inputs and assumptions.
- Source facts, engineering inference, recommendations, and owner-locked decisions must remain distinguishable.

## 4. No purchasing or release from concept geometry

Concept sketches may use envelopes, but they cannot become purchase-ready drawings, released DXFs, or final hole tables until the exact components are selected and verified.

Do not buy a major motion, control, torch-height, or plasma component merely because it appears in a concept BOM.

## 5. Guidance and drive are separate systems

Linear guides support and constrain motion. They do not propel an axis.

Every motion proposal must separately define:

- guidance;
- drive mechanism;
- motors and drives;
- feedback or position-loss detection;
- homing and gantry squaring;
- usable travel;
- guarding and contamination protection;
- service access;
- controller and software compatibility.

## 6. Compare retrofit and new-build options fairly

The existing SPX4300 table and a new compact X-1 are both valid candidates until the project owner locks one path.

Every comparison must account for:

- parts already owned;
- downtime of the existing large table;
- achievable contour quality and acceleration;
- work envelope;
- mechanical risk;
- control and THC integration;
- total delivered cost;
- fabrication time;
- reversibility and serviceability.

Do not bias the comparison merely because one option has already received more documentation.

## 7. Controls are selected by machine requirements

Jackpot/FluidNC, LinuxCNC/QtPlasmaC, Mesa hardware, and other control paths remain provisional until the project owner locks a platform.

A complete plasma-machine interface is required as a design target. A generic G-code sender alone is not treated as a finished operator system.

## 8. THC remains a required design target

Automatic closed-loop torch-height control remains an active design target, but its implementation is not locked.

Any proposed THC architecture must define:

- isolated arc-voltage sensing;
- Arc OK behavior;
- floating-head or ohmic probing;
- position-aware Z correction;
- corner and velocity anti-dive;
- void and cut-loss behavior;
- limits, faults, and recovery;
- live diagnostics and target voltage;
- safe failure behavior.

## 9. Safety functions do not live only in software

- E-stop must remove motion and torch-enable capability through hardware.
- Torch start must use verified isolation.
- Plasma voltage must never connect directly to controller electronics.
- Raw voltage is permitted only through a documented galvanically isolated high-voltage measurement interface rated for the real source and transients.
- Software limits supplement physical stops, guards, and electrical protection.

## 10. Reference files are read-only

Third-party plans, guides, and archives stay unchanged. They may be indexed, summarized, measured, and cited, but project manufacturing files must be original outputs based on verified hardware and requirements.

## 11. GitHub workflow

- `main` contains the accepted planning baseline, not necessarily locked decisions.
- Meaningful changes use a focused branch and pull request.
- One pull request should address one coherent study, correction, or deliverable.
- Pull requests must state what changed, why, assumptions, and validation performed.
- Issues track questions requiring measurements, research, cost comparison, design, testing, or owner selection.
- A merged PR records work; it does not lock the underlying choice.

## 12. Definition of done

A task is complete only when its stated acceptance criteria are met, evidence is stored in the correct location, assumptions are labeled, and the result answers the active planning question.
