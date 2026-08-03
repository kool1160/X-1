# X-1

**Laser X Design X-1 CNC Plasma Table**

X-1 is a compact precision plasma table designed to approach fiber-laser-like contour quality as closely as practical without fiber-laser cost.

It is optimized for:

- 10, 12, 14, 16, and 18 gauge mild steel;
- intricate signs and decorative profiles;
- smooth curves and crisp direction changes;
- small holes and internal features within realistic plasma limits;
- repeatable touch-off, cut height, and THC behavior;
- low dross and minimal cleanup.

X-1 is not an exact CrossFire PRO replica and it does not replace the existing large plasma table. The CrossFire PRO guide remains a packaging and assembly reference only.

## Locked mechanical direction

- welded tube structure using available 1/8-inch-wall material;
- one-piece welded water pan;
- profile linear rails on X and both Y sides;
- recirculating ball screws on X, Y-left, and Y-right;
- independent dual-Y homing and squaring;
- closed-loop stepper or AC-servo drives;
- precision powered Z;
- floating touch-off head;
- separate torch breakaway;
- protected rails, screws, nuts, and lubrication points.

ACME main-axis screws and bearings running directly on structural tube are excluded.

## Plasma and control direction

The finished cut quality depends on the torch and process as much as the machine motion. The production architecture must include:

- a machine torch and consumable system suited to fine cutting;
- dry, stable compressed air;
- isolated torch start and Arc OK;
- closed-loop arc-voltage THC;
- velocity/corner anti-dive;
- material profiles and cut charts;
- small-hole velocity reduction and overcut support;
- a complete plasma-machine operator interface.

The current leading control architecture is **LinuxCNC + QtPlasmaC** with deterministic Ethernet motion hardware and an isolated arc-voltage interface.

The existing Everlast PowerPlasma 82i may be used for development, but the final source/torch/consumable package remains open because motion accuracy cannot compensate for a wide or unstable plasma arc.

## Start here

1. [Project summary](PROJECT_SUMMARY.md)
2. [Current project status](docs/PROJECT_STATUS.md)
3. [Locked decisions](docs/DECISION_LOG.md)
4. [Design requirements](docs/REQUIREMENTS.md)
5. [Cut-quality targets](docs/CUT_QUALITY_TARGETS.md)
6. [Project rules](docs/PROJECT_RULES.md)
7. [THC architecture](docs/THC_ARCHITECTURE.md)

## Current phase

**Phase 1 — Precision Motion, Plasma Process, and Control Freeze**

No Rev B manufacturing package will be released until the exact rails, ball screws, motors/drives, Z components, plasma source/torch/consumables, controller, I/O, and THC hardware are selected from verified drawings or measurements.

## Repository map

- [`docs/`](docs/) — status, scope, requirements, decisions, process targets, and architecture
- [`references/`](references/) — source index and usage rules
- [`cad/`](cad/) — native SolidWorks models
- [`drawings/`](drawings/) — released PDFs, DXFs, hole tables, and manufacturing outputs
- [`bom/`](bom/) — component research and released BOMs
- [`firmware/`](firmware/) — controller configuration and controlled firmware work
- [`software/`](software/) — optional X-1 companion software where it adds value
- [`testing/`](testing/) — motion, cut-quality, alignment, commissioning, and validation records

## Safety

This repository is an engineering-development workspace, not a certification. Plasma arc voltage, mains power, automatic motion, fumes, fire, hot material, pinch points, and UV/IR exposure can cause severe injury or death. The finished machine requires verified isolation, grounding, hardwired emergency-stop behavior, guarding, ventilation, fire controls, and confirmed plasma-interface pinouts before operation.
