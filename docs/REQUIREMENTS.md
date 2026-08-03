# X-1 Design Requirements

## 1. Mechanical replica target

- X-1 shall reproduce the standard CrossFire PRO mechanical architecture rather than the PRO MAX or the earlier custom 50 × 50 concept.
- Published target cutting envelope: **48.25 in X × 33.3 in Y**.
- Published target floor space: approximately **54.2 in × 69.5 in**.
- The machine shall support/pass a full 4-foot-wide sheet in the same manner as the CrossFire PRO.
- The final released assembly shall reproduce the published work envelope without carriage, nut, coupler, bearing, cable, or hard-stop interference.
- Any deviation required for Jackpot, FluidNC, X-1 Control, or X-1 THC shall be limited to controls, wiring, enclosure, and interface hardware unless a mechanical interference is documented.

## 2. Frame and water table

- Reproduce the CrossFire PRO lower tube frame, four legs, lower rails, cross tubes, stanchion layout, gussets, side skirts, and leveling-foot arrangement.
- Use available steel of equal or greater section strength while preserving the verified external geometry and mounting relationships.
- Reproduce the two-piece stainless water-table arrangement or a one-piece welded tray with the same verified internal and external dimensions.
- Water-table, drains, slat holders, and slats shall reproduce the verified PRO layout.
- The water tray and material load shall not distort the motion rails.
- Frame squareness and Y-rail parallelism shall be adjusted to at least the assembly-guide requirement of **1/32 inch**.

## 3. Linear guidance

- Y guidance shall use zinc-plated steel tube rails and adjustable rolling ball-bearing carriages patterned after the CrossFire PRO.
- Each Y side shall use the same fixed/adjustable bearing arrangement and preload method as the reference machine unless an equivalent metal implementation is dimensionally documented.
- X guidance shall use the CrossFire PRO gantry tube and rolling carriage architecture.
- Bearings, eccentric adjusters, backing plates, fasteners, and preload access shall remain serviceable.
- Rails and bearings shall be protected from direct slag, abrasive dust, and water splash without reducing the verified travel.

## 4. Main-axis drive system

- The main axes shall use multi-start ACME lead screws, not ball screws.
- Y-left and Y-right shall each use **3/8-8, 4-start ACME** screws with acetal anti-backlash nuts.
- X shall use a **1/2-10, 5-start ACME** screw with an acetal anti-backlash nut.
- Every main screw shall advance **0.5 inch per revolution**.
- Each main screw shall use an OEM-equivalent turned motor journal, clamping motor coupler, and opposite-end 608 bearing support.
- Lead-nut mounts shall allow the controlled float used during alignment, then lock after the carriage is squared.
- Exact screw lengths, journal dimensions, tapped-end details, coupler bores, and nut-mount hole patterns shall be verified before purchase or release.
- The released drive system shall support the published 300 ipm maximum cut-speed capability or document a tested equivalent.

## 5. Motors and Z axis

- X, Y-left, and Y-right shall use NEMA 23 motors equivalent to the published **284 oz-in** specification.
- Z shall use a NEMA 23 motor equivalent to the published **180 oz-in** specification.
- Z shall reproduce the powered floating-head and initial-height-sensing functions of the CrossFire PRO.
- Target Z capability is the published **2.75 inches powered travel plus 3 inches manual adjustment**.
- The Z slide, torch mount, IHS switch, floating travel, and cable-strain-relief geometry shall be reconstructed and verified.
- The Z screw specification may differ from the main axes but shall be documented and serviceable.

## 6. Controls boundary

- Langmuir electronics, FireControl, and Langmuir computer hardware are excluded.
- Baseline controller is the V1 Engineering Jackpot CNC Controller V1.2.1.
- Baseline firmware is FluidNC or a controlled X-1 FluidNC fork required to meet locked requirements.
- X, Y-left, Y-right, and Z require independent motor channels.
- The configuration and any X-1 firmware changes shall be stored in this repository.
- Separate left/right Y homing or a documented squaring procedure shall reproduce reliable gantry square.
- Hardware safety shall not depend solely on the Windows application.

## 7. Operator software

- The finished machine shall use dedicated **X-1 Control** software, not FireControl, a generic G-code sender, or only the stock FluidNC WebUI.
- FluidNC shall own embedded motion, stepping, limits, homing, probing inputs, local job execution, and controller-side THC functions.
- X-1 Control shall provide machine setup, jogging, job import/preview/validation, work offsets, trace, dry run, run/hold/resume/stop, alarms, logs, material profiles, recovery, diagnostics, and THC controls/status.

## 8. Plasma interface

- Torch start shall use verified isolated dry contacts.
- Arc OK shall enter only through a verified isolated interface.
- The Everlast divided-voltage output shall never connect directly to Jackpot or ESP32 GPIO.
- DV polarity, physical divider ratio, loaded behavior, and maximum expected output shall be verified.
- The meter-induced voltage-reading change observed on the existing table shall be reproduced and explained before X-1 voltage-interface approval.

## 9. Torch height control

- The completed X-1 shall include automatic closed-loop arc-voltage THC.
- The THC architecture shall keep FluidNC Z position synchronized with all corrections.
- It shall include Arc OK gating, stabilization delay, target-voltage control, deadband/control law, correction limits, corner/velocity anti-dive, cut-loss behavior, fault handling, and operator status/control.
- Production release is blocked until THC is validated on representative warped material without torch dive or accumulated Z-position error.

## 10. Safety and serviceability

- E-stop shall remove motion and torch-enable capability through hardware.
- Motor couplers, lead nuts, bearings, switches, drains, and wiring terminations shall be accessible for adjustment and replacement.
- Guards shall cover exposed screws and pinch points without preventing alignment or maintenance.
- The electronics enclosure shall separate mains, motor power, controller, plasma interface, and low-level signals.
- Grounding, bonding, strain relief, ventilation, fire control, and safe material handling are required.

## 11. Documentation and exactness

The attached assembly guide is an assembly source, not a complete manufacturing drawing package. Rev B shall include:

- source-evidence matrix identifying published, measured, derived, and inferred dimensions;
- complete SolidWorks assembly with verified work envelope;
- tube cut list and hole tables;
- carriage, stanchion, gantry, mount, gusset, skirt, tray, slat-holder, and Z drawings;
- ACME screw end-machining drawings and nut/coupler/bearing interfaces;
- released DXFs and PDFs;
- mechanical BOM and supplier references;
- wiring and I/O diagrams for Jackpot/FluidNC;
- X-1 Control and THC interface specifications;
- alignment, break-in, and commissioning checklist.

No unverified hole pattern or hidden dimension may be labeled exact. Inferred dimensions must be clearly marked until validated against a physical machine, OEM drawing, or closed-loop assembly measurement.
