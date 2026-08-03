# X-1 Project Rules

These rules exist to prevent scope drift, invented dimensions, duplicated work, and premature fabrication. They apply to mechanical design, controls, software, documentation, purchasing, and testing.

## 1. One active phase

Only the work listed in [`PROJECT_STATUS.md`](PROJECT_STATUS.md) is active.

A useful idea outside the active phase is recorded in [`PARKING_LOT.md`](PARKING_LOT.md). It is not researched, designed, coded, purchased, or added to the current release unless the active phase is formally changed.

## 2. Authority order

When documents disagree, use this order:

1. `PROJECT_STATUS.md` for current phase and priority
2. `DECISION_LOG.md` for locked decisions
3. `REQUIREMENTS.md` for mandatory design constraints
4. `PROJECT_RULES.md` for process and scope control
5. `ARCHITECTURE.md` and subsystem documents for implementation direction
6. released X-1 drawings, BOMs, configurations, and test records
7. third-party references for ideas only

A reference machine never overrides an X-1 requirement or a verified purchased-part dimension.

## 3. No hidden assumptions

- Mark every unverified dimension as `TBD`, `ASSUMPTION`, or `REFERENCE ONLY`.
- Do not release a mounting pattern from a seller photograph, generic model, or nominal family dimension.
- Use verified manufacturer drawings or measurements from the actual component.
- Calculations must state their inputs and assumptions.
- Source-derived facts, engineering inference, and new design decisions must remain distinguishable.

## 4. Exact hardware before final CAD

No Rev B dimension-critical CAD or manufacturing output until the exact guides, blocks, drive components, motors/drivers, and Z hardware are selected.

Concept sketches may use envelopes, but they cannot become released DXFs, hole tables, or purchase-ready drawings until the selected components are modeled or measured.

## 5. Guides and drives remain separate decisions

Linear guides support and constrain motion. They do not propel the axes.

Every guide proposal must identify the separate drive system. Every drive proposal must identify how it mounts beside the selected guides and how it affects usable travel, guards, service access, and motor sizing.

## 6. Locked decisions stay locked

A locked decision changes only when new evidence materially affects cost, safety, performance, availability, or manufacturability.

Changing a locked decision requires:

1. a GitHub issue describing the reason;
2. comparison against the current decision;
3. a new decision-log entry that preserves the old history;
4. updates to affected requirements, status, architecture, and drawings.

Casual brainstorming does not change the project baseline.

## 7. No controller drift during the prototype phase

The prototype baseline is the existing Jackpot controller with FluidNC and dedicated X-1 operator software.

Mesa, LinuxCNC, EtherCAT, custom motion firmware, and other controller paths remain parked unless the current system fails a documented requirement or the project owner explicitly reopens the controller decision.

Custom FluidNC work specifically required to deliver X-1 THC is not controller drift. It is allowed only after the THC architecture is selected and its firmware boundary is documented.

## 8. Operator software is a machine subsystem

X-1 will not rely on a generic G-code sender for normal operation.

The dedicated operator application must remain separate from FluidNC's real-time motion responsibilities. It may command and monitor the controller, but hardwired safety, limits, and controller-side behavior cannot depend solely on the Windows application.

During Phase 1, software work is limited to requirements, protocol investigation, architecture, and a communication proof of concept. Full production features wait for the machine I/O, motion configuration, and operating sequence to be frozen.

## 9. THC is required, but commissioned in stages

The finished X-1 requires automatic closed-loop torch-height control. THC is not optional and is not in the parking lot.

The project may prove motion, probing, torch firing, and fixed-height cutting first because that isolates mechanical, CAM, and plasma-interface faults. That intermediate test does not satisfy the final machine requirement.

Before the THC architecture is locked, it must define:

- isolated arc-voltage sensing;
- verified divider ratio and polarity;
- target-voltage control method;
- real-time Z correction path compatible with FluidNC;
- Arc OK behavior;
- corner and velocity anti-dive;
- void/cut-loss response;
- enable, disable, delay, and fault behavior;
- operator display, setpoint, diagnostics, and logging;
- safe response to communication or sensor failure.

Production release is blocked until THC has been integrated and validated on real cuts.

## 10. Safety functions do not live only in software

- E-stop must remove motion and torch-enable capability through hardware.
- Torch start must use verified isolation.
- No raw or divided arc-voltage signal may connect directly to Jackpot GPIO.
- Software limits supplement physical stops and guards.
- The operator application may display and command safety-related states but cannot be the only protective layer.

## 11. Reference files are read-only

Third-party plans, guides, and archives stay unchanged. They may be indexed, summarized, and cited, but X-1 manufacturing files must be original project outputs based on verified requirements and hardware.

## 12. GitHub workflow

- `main` contains the current accepted project baseline.
- Meaningful changes use a focused branch and pull request.
- One pull request should address one coherent decision or deliverable.
- Every pull request states what changed, why, affected requirements, and validation performed.
- Do not merge unresolved `TBD` values into released manufacturing files.
- Issues are used for work that needs a decision, measurement, purchase, design, test, or deliverable.

## 13. Definition of done

A task is not complete because a document or model exists. It is complete only when its issue acceptance criteria are met, affected source-of-truth documents are updated, outputs are stored in the correct directory, and the result is reviewed against the active phase gate.
