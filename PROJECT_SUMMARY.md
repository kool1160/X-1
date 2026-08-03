# X-1 Project Summary

## Project

**X-1 — Laser X Design 1** is a compact, high-precision CNC plasma table intended to get as close as practical to fiber-laser-like contour quality without the cost of building or buying a fiber laser.

The machine is not an exact CrossFire PRO replica and is not intended to replace the existing large CNC plasma table. The large table handles size and heavy fabrication. X-1 is optimized for precision work, intricate signs, small internal features, smooth curves, and repeatable cutting in mild steel from **10 gauge through 18 gauge**.

## Realistic process boundary

X-1 can be engineered to minimize the mechanical and control errors that make ordinary plasma tables cut poorly, but conventional air plasma will not equal a fiber laser's kerf width, heat-affected zone, smallest feature size, or absolute tolerance.

The design goal is therefore:

- fiber-laser-like motion quality and repeatability;
- the narrowest practical plasma kerf;
- excellent contour fidelity and corners;
- consistent touch-off and cut height;
- strong small-hole and small-arc behavior;
- minimum dross and secondary cleanup;
- repeatable results across 10, 12, 14, 16, and 18 gauge mild steel.

The finest-detail expectations apply primarily to 14–18 gauge. The 10–12 gauge requirement is clean, accurate, reliable profile cutting rather than pretending every laser-scale feature will transfer unchanged to thicker plasma cuts.

## Mechanical baseline

- compact half-sheet-class footprint;
- available 1/8-inch-wall tube for the main structure;
- one-piece welded water pan and replaceable slat system;
- profile linear rails on X and both Y sides;
- recirculating ball screws on X, Y-left, and Y-right;
- independent Y motors and homing for automatic gantry squaring;
- closed-loop stepper or AC-servo motion, selected from actual inertia, speed, and acceleration calculations;
- precision powered Z with floating touch-off, mechanical overtravel, and separate torch breakaway;
- protected rails, screws, nuts, and lubrication points.

The CrossFire PRO guide remains useful for compact packaging, dual-Y arrangement, water/slat concepts, floating-head purpose, and assembly order. Its ACME screws and tube-running rolling carriages are not part of the X-1 precision architecture.

## Plasma and controls baseline

The quality target depends on more than the frame. X-1 must treat the complete cutting process as one system:

- rigid low-backlash motion;
- dry, stable compressed air;
- appropriate machine torch and low-amperage/fine-cut consumables;
- accurate pierce height, cut height, and torch timing;
- closed-loop arc-voltage THC with velocity/corner anti-dive;
- small-hole velocity reduction and overcut support;
- material-specific cut charts and repeatable consumable setup;
- a mature plasma-machine operator interface.

Two plasma sources are already on hand:

- **LOTOS LTP5500DCNC** with machine torch: 20–55 A on 220/240 V, 20–35 A on 110/120 V, non-HF blowback pilot arc, a CNC torch-start interface, and a separate **1:1 raw arc-voltage/THC output**. It is the baseline production candidate because it previously ran on the JD's Garage table and already provides the core machine-facing functions X-1 needs. The raw-voltage output requires a properly engineered isolated high-voltage divider or THCAD interface. Arc OK availability and pinout must be verified on this exact unit rather than assumed.
- **Everlast PowerPlasma 82i** with machine torch: retained as the higher-amperage development and comparison source.

Neither source is declared production-ready until controlled 10–18 gauge coupon testing establishes kerf, dross, angularity, pierce consistency, small-feature behavior, consumable life, and repeatability.

## Current control direction

The leading architecture is:

- LinuxCNC;
- QtPlasmaC;
- deterministic Ethernet motion hardware;
- isolated torch-start and Arc OK interfaces;
- isolated divided-voltage measurement for THC.

The Jackpot and FluidNC remain available for testing or another machine, but they will not be forced into X-1 unless they prove the complete plasma requirements without requiring us to recreate a mature THC and plasma-control stack.

## Active phase

**Phase 1 — Precision Motion, Plasma Process, and Control Freeze**

Immediate work:

1. Freeze practical sheet-support and cutting-envelope targets.
2. Select exact profile rails and bearing blocks.
3. Select X and Y ball-screw diameter, lead, length, supports, and nuts.
4. Select closed-loop steppers or AC servos.
5. Bench-test the LOTOS and Everlast source/torch/consumable packages across 10–18 gauge and select the production process.
6. Select LinuxCNC/QtPlasmaC motion and isolated THC hardware.
7. Design the one-piece water pan, floating touch-off Z, and torch breakaway.
8. Build the Rev B SolidWorks assembly and validation plan.

## Sources of truth

Read in this order:

1. [`docs/PROJECT_STATUS.md`](docs/PROJECT_STATUS.md)
2. [`docs/DECISION_LOG.md`](docs/DECISION_LOG.md)
3. [`docs/REQUIREMENTS.md`](docs/REQUIREMENTS.md)
4. [`docs/CUT_QUALITY_TARGETS.md`](docs/CUT_QUALITY_TARGETS.md)
5. [`docs/PROJECT_RULES.md`](docs/PROJECT_RULES.md)
6. [`docs/THC_ARCHITECTURE.md`](docs/THC_ARCHITECTURE.md)
7. original reference material
