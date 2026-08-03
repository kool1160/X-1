# CrossFire PRO Mechanical Baseline

## Purpose

This document separates verified CrossFire PRO mechanical facts from dimensions that still require reconstruction. It is the source-derived baseline for the X-1 mechanical replica.

## Source set

Primary:

- `CrossFire PRO Assembly Guide _ Langmuir Systems.pdf`
- official CrossFire PRO specifications page
- official Langmuir assembly and troubleshooting pages

Secondary:

- Langmuir user forum posts for screw pitch/starts and measured dimensions
- community measurements must be verified before manufacturing release

## Verified published specifications

| Item | Specification | Evidence class |
|---|---:|---|
| Cutting envelope X | 48.25 in | Published official |
| Cutting envelope Y | 33.3 in | Published official |
| Powered Z travel | 2.75 in | Published official |
| Manual Z adjustment | 3 in | Published official |
| Floor space | approximately 54.2 × 69.5 in | Published official |
| Machine weight | 223 lb | Published official |
| Guidance | Ball-bearing carriages on zinc-plated steel tube rails | Published official |
| Maximum cut speed | 300 ipm | Published official |
| X/Y motor torque | NEMA 23, 284 oz-in each | Published official |
| Z motor torque | NEMA 23, 180 oz-in | Published official |
| Slat section | 50 mm wide × 3 mm thick | Published official |

## Main-axis screws

These are **ACME lead screws**, not ball screws.

| Axis | Screw | Starts | Lead | Nut |
|---|---|---:|---:|---|
| Y-left | 3/8-8 ACME | 4 | 0.5 in/rev | Acetal anti-backlash |
| Y-right | 3/8-8 ACME | 4 | 0.5 in/rev | Acetal anti-backlash |
| X | 1/2-10 ACME | 5 | 0.5 in/rev | Acetal anti-backlash |

Assembly details:

- motor end uses a clamping coupler to a NEMA 23 motor;
- opposite end uses a 608 ball bearing;
- the bearing end is retained by a 10-32 screw and washer into a tapped screw end;
- lead-nut mounts remain loose during initial alignment and are tightened only after the gantry/carriage is positioned and squared;
- X motor and bearing mounts are shorter than the Y versions;
- the longer X screw uses the larger 1/2-inch diameter to reduce whip.

## Frame and motion parts identified by the guide

### Frame

- 4 leg tubes
- 2 lower cross tubes
- left and right lower rail tubes
- 2 Y-axis tube rails
- 8 stanchion plates
- 4 corner gussets
- 2 side skirts
- leveling-foot inserts and feet
- cable-support tube

### Motion

- left and right Y carriage weldments
- four Y bearing-block assemblies, two per carriage
- each Y bearing assembly includes fixed and adjustable bearing blocks
- gantry tube
- X/Z carriage assembly
- X motor mount
- X bearing mount
- 2 Y motor mounts
- 2 Y bearing mounts
- 2 Y anti-backlash nuts
- 1 X anti-backlash nut and floating mount tab
- 3 main-axis lead screws
- 3 main-axis NEMA 23 motors
- 3 motor couplers
- 3 608 support bearings

### Water table and slats

- two water-table half sections joined at the center seam
- two drain assemblies
- four slat holders
- sixteen slats

A community measurement reports the joined tray as approximately **36 × 52.5 × 2 inches**. Treat this as secondary evidence until checked against a physical tray or closed-loop model.

### Z and IHS

- powered Z slide
- floating torch mount
- fixed and floating V-blocks
- IHS normally closed switch
- torch contact opens the switch to establish plate surface
- torch cable requires enough slack to avoid false IHS activation

## Assembly and alignment sequence to reproduce

1. Install leveling feet in legs.
2. Loosely assemble lower frame.
3. Square lower rails to cross tubes.
4. Equalize rail spacing and hold parallelism within 1/32 in.
5. Assemble adjustable rolling-bearing carriages.
6. Install Y tube rails through carriages and stanchions.
7. Assemble gantry, X carriage, Z, motor mount, and bearing mount.
8. Attach gantry to Y carriages while fasteners remain loose.
9. Preload fixed/adjustable bearing blocks.
10. Drive gantry to stanchion references and tighten the gantry/carriage relationship.
11. Install and align water tray and slats.
12. Install motor mounts, bearing mounts, and floating lead nuts.
13. Thread screws through nuts and into support bearings.
14. Install motors and couplers.
15. Power motors for holding torque, tighten couplers, then tighten lead nuts after alignment.
16. Tram Z and validate IHS.

## Manufacturing dimensions still missing

The guide does not publish enough information for a guaranteed hole-for-hole replica. The following require measurement, CAD reconstruction, or additional drawings:

- tube outside dimensions, wall thicknesses, and exact cut lengths;
- all tube hole positions and diameters;
- stanchion plate size, thickness, bends, and hole pattern;
- Y rail tube length and mounting-hole pattern;
- carriage weldment plate sizes and bearing geometry;
- bearing type, diameter, eccentric hardware, and offsets;
- gantry tube section, length, cutouts, and hole pattern;
- X carriage geometry and bearing layout;
- exact screw overall lengths and motor/bearing-end machining;
- motor-mount, bearing-mount, and lead-nut-mount geometry;
- water-tray bend, flange, drain, and center-seam details;
- slat-holder slot spacing;
- Z screw, guides, bearing layout, switch geometry, and torch mount.

## Evidence classification

Every reconstructed dimension shall be tagged:

- **P — Published:** explicit OEM specification or assembly dimension.
- **M — Measured:** taken from a physical OEM part or machine.
- **D — Derived:** calculated from published/measured geometry and validated by assembly closure.
- **I — Inferred:** estimated from images or generic hardware; not releasable as exact.

No critical `I` dimension may remain in a released manufacturing drawing.
