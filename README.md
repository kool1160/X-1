# X-1

**Laser X Design X-1 CNC Plasma Table**

X-1 is a mechanically faithful replica of the **Langmuir CrossFire PRO frame and motion system**, paired with our own controls:

- Jackpot CNC controller
- FluidNC or a controlled X-1 FluidNC fork
- dedicated X-1 Windows operator software
- isolated torch interface and required automatic THC

We are copying the machine's frame, tube-rail carriages, gantry, ACME lead-screw drive, water table, slat bed, and floating Z architecture. We are **not** using Langmuir electronics, FireControl, their computer, or LS-THC.

## Verified mechanical baseline

- Cutting envelope: **48.25 in X × 33.3 in Y**
- Floor space: approximately **54.2 in × 69.5 in**
- X screw: **1/2-10, 5-start ACME**
- Y screws: **two 3/8-8, 4-start ACME**
- Screw advance: **0.5 in/revolution on every main axis**
- Lead nuts: acetal anti-backlash
- End support: 608 bearing
- Main motors: NEMA 23, 284 oz-in
- Z motor: NEMA 23, 180 oz-in
- Guidance: adjustable ball-bearing carriages on zinc-plated steel tube rails

These are lead screws, not ball screws.

## Start here

1. [Project summary](PROJECT_SUMMARY.md)
2. [Current project status](docs/PROJECT_STATUS.md)
3. [Locked decisions](docs/DECISION_LOG.md)
4. [Design requirements](docs/REQUIREMENTS.md)
5. [CrossFire PRO mechanical baseline](docs/CROSSFIRE_PRO_MECHANICAL_BASELINE.md)
6. [Project rules](docs/PROJECT_RULES.md)
7. [THC architecture](docs/THC_ARCHITECTURE.md)
8. [Operator-software architecture](docs/OPERATOR_SOFTWARE.md)

## Current phase

**Phase 1 — CrossFire PRO Mechanical Reconstruction**

The assembly guide provides the correct part relationships, hardware, screw sizes, bearing arrangement, motor arrangement, and assembly sequence. It does not provide every manufacturing dimension. The active job is to reconstruct and verify:

- tube cut lengths and hole locations
- Y rail and stanchion geometry
- rolling carriage plates and bearing positions
- gantry tube and X carriage
- motor, coupler, bearing, and lead-nut mounts
- water tray and slat-holder geometry
- floating Z dimensions and IHS mechanism

No hole-for-hole manufacturing drawing will be labeled exact until it is supported by a verified measurement, published dimension, or validated assembly geometry.

## Repository map

- [`docs/`](docs/) — scope, status, requirements, decisions, architecture, and reconstruction notes
- [`references/`](references/) — source index and usage rules
- [`cad/`](cad/) — native SolidWorks models
- [`drawings/`](drawings/) — released PDFs, DXFs, hole tables, and manufacturing outputs
- [`bom/`](bom/) — motion-component research and released BOMs
- [`firmware/fluidnc/`](firmware/fluidnc/) — Jackpot/FluidNC configuration and controlled firmware work
- [`software/`](software/) — X-1 operator application
- [`testing/`](testing/) — inspection, alignment, commissioning, and validation records

## Primary reference

- [CrossFire PRO Assembly Guide](CrossFire%20PRO%20Assembly%20Guide%20_%20Langmuir%20Systems.pdf)

The PRO MAX and JD's Garage files remain secondary references only. The standard CrossFire PRO is now the mechanical authority for the X-1 replica.

## Safety

This repository is an engineering-development workspace, not a certification. Plasma arc voltage, mains power, automatic motion, fumes, fire, hot material, pinch points, and UV/IR exposure can cause severe injury or death. The finished machine requires verified isolation, grounding, hardwired emergency-stop behavior, guarding, ventilation, fire controls, and confirmed plasma-interface pinouts before operation.
