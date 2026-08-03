# X-1 Cut-Quality Targets

## Purpose

X-1 is intended to approach fiber-laser-like contour quality as closely as practical using a compact plasma process. This document separates machine-performance targets from plasma-process limits so the project does not confuse precise motion with a narrow laser kerf.

All values below are engineering targets for validation, not released performance claims.

## Required material range

| Mild steel | Production requirement | Primary objective |
|---|---|---|
| 18 gauge | Required | finest detail, narrow kerf, minimal heat distortion |
| 16 gauge | Required | intricate signs, small internal features, clean corners |
| 14 gauge | Required | detailed signs and general precision fabrication |
| 12 gauge | Required | clean accurate profiles and useful small features |
| 10 gauge | Required | clean reliable profiles, holes, slots, and fabrication parts |

The finest-feature expectations apply to 14–18 gauge. Minimum feature size shall increase as material thickness and measured kerf increase.

## Reality boundary

X-1 shall not be advertised or documented as equal to a fiber laser in:

- kerf width;
- heat-affected zone;
- smallest stable feature;
- smallest high-quality hole;
- edge angularity;
- absolute dimensional tolerance.

The project succeeds when the table removes avoidable mechanical and process error so the remaining difference is mainly the plasma arc and consumable process.

## Provisional motion-system targets

These are measured at the torch centerline with the plasma off:

- bidirectional positioning repeatability target: **0.003 in or better**;
- measured reversal/backlash target: **0.002 in or better**;
- no lost position after repeated high-acceleration contour cycles;
- no visible screw whip, resonance, or gantry racking in the released speed range;
- repeatable dual-Y homing and squaring within the final documented tolerance;
- repeatable floating-head touch-off offset with recorded mean and spread;
- Z position remains synchronized through all THC corrections, holds, resumes, and faults.

These targets may be tightened after the exact rails, screws, motors, encoders, and controller are selected.

## Provisional finished-cut targets

After kerf compensation and material-profile tuning:

- 14–18 gauge dimensional goal: **within ±0.020 in** on representative profiles;
- 10–12 gauge dimensional goal: **within ±0.030 in** on representative profiles;
- circularity, corner quality, and hole quality must be assessed separately from overall size;
- dross should be absent or light and easily removable at the approved production setting;
- top-edge rounding and bevel shall be recorded photographically and by measurement where practical;
- no torch dives, plate contact, or accumulated Z error are permitted in production profiles.

These are project goals, not guarantees. Final released tolerances shall come from repeated controlled tests.

## No assumed minimum hole or feature

Do not use laser design rules for plasma parts.

For each gauge, controlled coupons shall determine:

- measured kerf width;
- minimum stable slot width;
- minimum isolated web width;
- minimum readable stencil bridge;
- minimum acceptable hole diameter;
- minimum internal-corner radius;
- lead-in and overcut requirements;
- distortion limits for closely spaced cuts.

The approved design rules shall be stored by material profile and consumable configuration.

## Process variables that must be recorded

Every test coupon shall record:

- plasma source and serial/configuration;
- machine torch;
- electrode, nozzle/cartridge, shield, swirl ring, and ohmic ring part numbers;
- consumable age and pierce count;
- material type, gauge, measured thickness, coating, and surface condition;
- amperage;
- air pressure and measured pressure stability;
- dryer/filter configuration;
- pierce height and delay;
- cut height;
- target arc voltage and THC delay;
- cut speed;
- small-hole percentage and overcut;
- lead-in type and length;
- kerf compensation;
- water level;
- ambient and material condition when relevant;
- photographs and measured results.

## Required test coupons

Each required gauge shall include:

1. straight cuts in both machine directions;
2. 1 in and 2 in squares;
3. 1 in and 2 in circles;
4. hole ladder from small to large diameter;
5. slot-width ladder;
6. internal and external corner test;
7. star or gear-like repeated reversal test;
8. text/stencil bridge test;
9. long diagonal;
10. dense decorative sign sample;
11. warped-sheet THC test;
12. repeated-part consistency test using fresh and aged consumables.

## Source-selection gate

The existing Everlast PowerPlasma 82i shall be tested first because it is already owned. It becomes the production source only if it meets the approved quality targets across the required gauges with repeatable consumable performance.

If it fails because of arc width, consumable options, pierce consistency, angularity, or repeatability, the project shall compare a mechanized fine-cut plasma source rather than redesigning precision motion around an unsuitable arc.

## Release rule

No minimum-feature chart, tolerance, cut speed, arc voltage, or kerf value is released until it is supported by repeated test coupons under a documented configuration.
