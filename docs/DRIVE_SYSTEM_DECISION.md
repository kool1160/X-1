# X-1 X/Y Drive-System Decision

## First principle

**Linear rails guide the machine. They do not drive it.**

The X-1 needs both:

1. a guide system that carries and constrains the moving assembly; and
2. a drive system that produces motion.

The current guide direction is purchased linear guides with metal carriage plates. The open question is whether X and Y are driven by rack and pinion, timing belts, or ball screws.

## Reference designs

- The JD's Garage reference package uses belt-drive components and a low-cost tube-frame approach.
- The CrossFire PRO MAX assembly guide uses long screws on X and both Y sides and provides useful alignment and floating-nut lessons.
- The X-1 Rev A plan recommends evaluating rack and pinion as the baseline while keeping belt and ball screw as alternatives.

These references demonstrate workable architectures but do not determine the final X-1 choice.

## Option comparison

| Criterion | Rack and pinion | Timing belt | Ball screw |
|---|---|---|---|
| Long-axis cost | Moderate | Lowest | Can jump sharply with length |
| Standard-length flexibility | Excellent | Excellent | Limited by available screw tiers |
| Speed/acceleration | Excellent | Excellent | Good if diameter/pitch avoid whip |
| Backlash control | Good with spring preload | Good with proper tension | Excellent with preloaded nut |
| Contamination tolerance | Good with guarding | Good with guarding | Most sensitive to slag/dust |
| Alignment difficulty | Moderate | Moderate | Highest on long dual screws |
| Maintenance | Mesh/preload/grease | Tension and belt inspection | Lubrication, support alignment, contamination control |
| Independent dual Y | Straightforward | Straightforward | Straightforward but synchronization/alignment matter |
| Easy field replacement | Good | Excellent | Depends on screw machining and exact nut/support |
| Best fit for very long travel | Strong | Strong | Requires careful length/diameter/speed selection |

## Ball-screw questions that must be answered

A nominal six-foot screw does not automatically provide six feet of cutting travel. Before designing around a screw, record:

- overall screw length;
- usable threaded length;
- end-machining dimensions;
- fixed and floating support widths;
- motor/coupler or pulley length;
- ball-nut body and flange dimensions;
- desired overtravel and switch clearance;
- screw diameter and lead;
- supported critical speed at the intended rapid speed;
- whether the screw rotates or the nut rotates;
- delivered price for two matched Y screws and one X screw.

The machine envelope shall be calculated from the actual purchased geometry rather than the advertised nominal length.

## Rack-and-pinion questions

- Mod or diametral pitch and pressure angle
- Rack section length and joint strategy
- Pinion tooth count and resulting travel per revolution
- Spring-loaded or eccentric preload method
- Gear reduction required for the selected motor
- Rack mounting surface and protective cover
- Lubrication and debris-management method

## Belt-drive questions

- Belt pitch and width
- Open-loop fixed-belt or moving-belt architecture
- Reduction ratio
- Tensioning method and adjustment range
- Long-span resonance/stretch
- Guarding and slag protection
- Readily available replacement belt length

## Current decision rule

Do not choose by theoretical precision alone. Plasma cut accuracy is limited by kerf, torch condition, plate movement, heat, frame alignment, and cut parameters. The preferred system is the one that gives the X-1:

- repeatable motion;
- adequate acceleration;
- easy alignment;
- affordable standard parts;
- good protection from plasma debris;
- simple replacement several years from now;
- compatibility with FluidNC and independent dual-Y homing.

## Decision gate

Collect one complete, purchasable component set for each serious option. Each set must include all three axes of drive hardware, supports, couplers/pulleys, motors or reduction parts, guarding needs, and delivered cost.

The final selection will be recorded in `docs/DECISION_LOG.md` before Rev B geometry is released.
