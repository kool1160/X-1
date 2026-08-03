# Contributing to X-1

X-1 is a controlled engineering project. Contributions are welcome when they advance the active phase and follow the project sources of truth.

## Before starting work

Read:

1. `PROJECT_SUMMARY.md`
2. `docs/PROJECT_STATUS.md`
3. `docs/DECISION_LOG.md`
4. `docs/REQUIREMENTS.md`
5. `docs/PROJECT_RULES.md`

Confirm the work is either tied to an open active issue or explicitly added to `PROJECT_STATUS.md`. Ideas outside the active phase belong in `docs/PARKING_LOT.md`.

## Branches

Use one focused branch per coherent task.

Suggested names:

- `research/linear-guides`
- `decision/drive-system`
- `design/y-truck`
- `firmware/thc-bench`
- `software/fluidnc-transport`
- `test/gantry-squaring`
- `docs/project-status`

Do not combine unrelated mechanical, electrical, firmware, and software changes in one pull request.

## Pull requests

Every pull request must state:

- problem or requirement addressed;
- linked issue;
- active phase;
- exact files and subsystems affected;
- assumptions and unverified items;
- calculations, drawings, measurements, or test evidence;
- impact on requirements, decisions, BOM, wiring, firmware, software, and tests;
- rollback or recovery plan when the change affects machine operation;
- validation performed and remaining risks.

A pull request that changes a locked decision must include the decision-change process defined in `docs/PROJECT_RULES.md`.

## Engineering evidence

Acceptable evidence includes:

- verified manufacturer drawings;
- measurements from the actual purchased part;
- calculations with stated inputs;
- controlled bench-test results;
- machine-test logs;
- photographs tied to a documented configuration;
- source code tests and reproducible communication logs.

Seller photographs, nominal product-family dimensions, and unsupported memory are not enough for released hole patterns or control interfaces.

## CAD and drawings

- Keep native SolidWorks files under `cad/`.
- Put released manufacturing outputs under `drawings/`.
- Mark nonreleased work clearly.
- Do not release dimension-critical DXFs or drawings with unresolved `TBD` values.
- Every released part must have a part number and revision.
- Actual purchased components must be modeled or measured before mounting holes are released.

## Firmware and software

- Back up known-good FluidNC firmware and configuration before changes.
- Record exact firmware version, board revision, configuration, and test hardware.
- Keep transport/protocol logic separate from the X-1 operator UI.
- Hardware safety cannot depend solely on the Windows application.
- THC firmware work must follow `docs/THC_ARCHITECTURE.md` and preserve position-aware Z control.

## Testing

- Use the test record template under `testing/`.
- Test with the plasma disconnected before live torch operation.
- Use a safe low-voltage simulator before connecting arc-voltage inputs.
- Record expected result, actual result, configuration, pass/fail, and corrective action.
- A change affecting motion, torch control, THC, limits, homing, or E-stop must include failure-mode testing.

## Merge rule

A change is ready to merge only when:

- it serves the active phase;
- linked acceptance criteria are met;
- affected source-of-truth documents are updated;
- no hidden assumptions remain in released outputs;
- validation evidence is committed or linked;
- the project can be restored to the prior known-good state if needed.
