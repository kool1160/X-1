## Purpose

What problem, requirement, or issue does this change address?

Closes #

## Active phase

- [ ] This work is listed in `docs/PROJECT_STATUS.md`
- [ ] Or the status/scope change is included in this pull request

## Change summary

Describe the mechanical, electrical, firmware, software, documentation, or test changes.

## Evidence

List the drawings, measurements, calculations, datasheets, logs, photographs, or tests supporting the change.

## Assumptions and TBDs

List every remaining assumption or unverified item. Use `None` when there are none.

## Impact check

- [ ] `docs/DECISION_LOG.md` reviewed/updated
- [ ] `docs/REQUIREMENTS.md` reviewed/updated
- [ ] `docs/PROJECT_STATUS.md` reviewed/updated
- [ ] BOM reviewed/updated
- [ ] CAD/drawings reviewed/updated
- [ ] Wiring/I/O reviewed/updated
- [ ] FluidNC configuration/firmware reviewed/updated
- [ ] X-1 operator software reviewed/updated
- [ ] THC architecture reviewed/updated
- [ ] Test and commissioning documents reviewed/updated

## Validation

What was tested, with what configuration, and what were the results?

## Failure and rollback

How does the machine fail safely, and how can this change be reverted to the previous known-good condition?

## Release check

- [ ] No dimension-critical pattern is based only on a seller photo or generic nominal dimension
- [ ] No arc-voltage signal is connected directly to Jackpot/ESP32 GPIO
- [ ] Hardware safety remains independent of the Windows application
- [ ] No unrelated parked feature was pulled into the active phase
- [ ] Linked issue acceptance criteria are satisfied
