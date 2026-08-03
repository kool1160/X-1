# X-1

**Laser X Design X-1 CNC Plasma Table**

X-1 is a clean-sheet CNC plasma table built around available 1/8-inch-wall tube, laser-cut/formable metal parts, purchased linear guides, a V1 Engineering Jackpot controller, FluidNC, required automatic THC, and dedicated X-1 operator software.

The project uses the JD's Garage and CrossFire PRO MAX files as references. X-1 is not a direct copy. Released parts and software must come from verified X-1 requirements, selected hardware, measurements, calculations, and testing.

## Start here

Read these before designing, purchasing, coding, or fabricating:

1. [Project summary](PROJECT_SUMMARY.md)
2. [Current project status](docs/PROJECT_STATUS.md)
3. [Locked decisions](docs/DECISION_LOG.md)
4. [Design requirements](docs/REQUIREMENTS.md)
5. [Project rules](docs/PROJECT_RULES.md)
6. [System architecture](docs/ARCHITECTURE.md)
7. [THC architecture](docs/THC_ARCHITECTURE.md)
8. [Operator-software architecture](docs/OPERATOR_SOFTWARE.md)

`PROJECT_STATUS.md` is the current-work authority. Ideas outside that active phase go into the [parking lot](docs/PARKING_LOT.md) instead of changing the project direction.

## Current phase

**Phase 1 — Architecture and Component Freeze**

Current objective: select the exact guide, drive, motor/driver, Z-axis, and THC architecture needed to freeze the work envelope and start the Rev B manufacturing package.

Current baseline:

- at least 48-inch material width;
- approximately 60–72 inches of Y cutting travel, finalized from affordable standard components;
- welded 1/8-inch-wall tube structure;
- purchased X/Y linear guides and metal structural carriages;
- independent Y-left/Y-right drive and automatic squaring;
- Jackpot controller with FluidNC;
- Everlast PowerPlasma 82i;
- dedicated Windows X-1 operator application;
- automatic closed-loop arc-voltage THC required for the finished machine.

Fixed-height cutting is an intermediate commissioning test. X-1 is not considered complete until the selected THC system is integrated and validated.

## Open architecture decisions

- Y guide family and exact length
- X guide family and exact length
- X/Y drive: rack and pinion, timing belt, or ball screw
- motor and driver strategy
- Z-axis guide and drive
- FluidNC-compatible THC hardware and firmware boundary
- operator-software implementation stack after the communication proof

No dimension-critical Rev B drawing is released until the exact purchased components are selected and verified.

## Repository map

- [`docs/`](docs/) — scope, status, requirements, decisions, architecture, and development plan
- [`references/`](references/) — reference index and usage rules
- [`cad/`](cad/) — native SolidWorks models
- [`drawings/`](drawings/) — released PDFs, DXFs, hole tables, and manufacturing outputs
- [`bom/`](bom/) — component research and released bills of material
- [`firmware/fluidnc/`](firmware/fluidnc/) — FluidNC configuration and controlled firmware work
- [`software/`](software/) — X-1 operator application
- [`testing/`](testing/) — inspection, alignment, commissioning, and validation records

## Primary references

- [X-1 Preliminary Engineering and Build Plan — Rev A](X-1_CNC_Plasma_Table_Preliminary_Build_Plan_Rev_A.pdf)
- [CrossFire PRO MAX Assembly Guide](CrossFire%20PRO%20MAX%20Assembly%20Guide%20_%20Langmuir%20Systems.pdf)
- [JD's Garage Imperial reference package](Imperial%20Version-20260802T230932Z-1-001.zip)

These are reference materials, not released X-1 manufacturing authority. Verify third-party licensing before redistribution.

## Safety

This repository is an engineering-development workspace, not a certification. Plasma arc voltage, mains power, automatic motion, fumes, fire, hot material, pinch points, and UV/IR exposure can cause severe injury or death. The finished machine requires verified isolation, grounding, hardwired emergency-stop behavior, guarding, ventilation, fire controls, and confirmed plasma-interface pinouts before operation.
