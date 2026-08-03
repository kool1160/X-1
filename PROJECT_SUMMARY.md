# X-1 Project Summary

## Project

**X-1 — Laser X Design 1** is a purpose-built CNC plasma table designed around available 1/8-inch-wall steel tube, laser-cut and formed metal parts, purchased linear guides, a V1 Engineering Jackpot controller, FluidNC motion firmware, and dedicated X-1 operator software.

X-1 is not a direct copy of the JD's Garage or Langmuir machines. Those files are references for proportions, assembly methods, alignment practices, drive concepts, water-table construction, and component ideas. Released X-1 parts must be designed from verified X-1 requirements and the exact hardware selected for this build.

## Current baseline

- Minimum material width: 48 inches
- Target Y cutting travel: approximately 60–72 inches, finalized from affordable standard component lengths
- Main frame: welded 1/8-inch-wall steel tube
- Exterior appearance: removable laser-cut skins and guards around the tube structure
- X/Y guidance: purchased linear guides with metal structural carriages
- Gantry: independent left and right Y drives with separate homing switches for automatic squaring
- Controller: V1 Engineering Jackpot CNC Controller V1.2.1
- Motion firmware: FluidNC
- Operator software: dedicated Windows X-1 machine application, not merely a generic G-code sender
- Plasma source: Everlast PowerPlasma 82i
- Initial cutting mode: probing plus fixed cut height; active arc-voltage THC is deferred until the base machine is reliable

## Active phase

**Phase 1 — Architecture and Component Freeze**

The project is currently selecting exact guides, drive components, motors/drivers, Z-axis hardware, and standard lengths. The frame envelope, mounting patterns, Rev B manufacturing drawings, FluidNC machine configuration, and production operator software remain blocked until those selections are verified.

## Active work, in order

1. Inventory reusable controller, motors, drives, power supplies, switches, relays, and enclosure hardware.
2. Select exact X and Y guide packages and rail lengths.
3. Select the complete X/Y drive architecture and actual components.
4. Select the Z-axis guide and drive.
5. Freeze usable travel, overall envelope, motor/driver strategy, and I/O requirements.
6. Release Rev B CAD, drawings, BOM, wiring, FluidNC configuration, and operator-software implementation plan.

## Not active yet

The following are deliberately deferred so the project does not drift:

- active arc-voltage THC integration;
- custom THC firmware;
- controller migration to Mesa, LinuxCNC, EtherCAT, or another platform;
- fiber-laser development;
- 4×8 expansion beyond the selected standard component tier;
- rotary-axis development;
- full CAM, nesting, quoting, cloud, mobile, or AI features;
- commercial production or sales packaging.

Deferred ideas belong in [`docs/PARKING_LOT.md`](docs/PARKING_LOT.md), not in the active phase.

## Sources of truth

Read these in order:

1. [`docs/PROJECT_STATUS.md`](docs/PROJECT_STATUS.md) — current active phase, blockers, and next work
2. [`docs/DECISION_LOG.md`](docs/DECISION_LOG.md) — locked decisions
3. [`docs/REQUIREMENTS.md`](docs/REQUIREMENTS.md) — mandatory design requirements
4. [`docs/PROJECT_RULES.md`](docs/PROJECT_RULES.md) — scope and workflow rules
5. [`docs/ARCHITECTURE.md`](docs/ARCHITECTURE.md) — system architecture
6. [`docs/OPERATOR_SOFTWARE.md`](docs/OPERATOR_SOFTWARE.md) — machine-software architecture
7. reference files — useful examples, but not X-1 manufacturing authority

## Phase 1 completion gate

Phase 1 is complete only when exact guide, drive, motor/driver, and Z components are selected; verified drawings or physical measurements exist; usable travel is calculated; the decision log is updated; and the architecture can be modeled without inventing dimension-critical details.
