# X-1 Design Requirements

## 1. Machine mission

- X-1 shall be a compact CNC plasma machine optimized for intricate 16-gauge and 18-gauge signs, delicate profiles, small interior features, clean corners, and repeatable thin-sheet cutting.
- X-1 is not intended to replace the existing large CNC plasma table. Compactness and precision take priority over maximum sheet length.
- The CrossFire PRO assembly guide remains a packaging and assembly reference only. X-1 shall not copy motion components that conflict with the precision objective.

## 2. Frame and one-piece water bed

- Main structure shall use available 1/8-inch-wall steel tube wherever practical.
- The machine shall use a one-piece welded water pan with welded drains and replaceable slat holders.
- Pan welding and support shall not distort the precision rail mounting surfaces. Rail pads shall be isolated, bolted, shimmed, machined, epoxy-leveled, or otherwise adjustable after welding.
- The motion frame shall be measured for diagonal equality, twist, and rail-pad straightness after all structural and pan welding is complete.
- Exterior guards and cosmetic panels shall be removable and nonstructural.

## 3. Precision linear guidance

- X and both Y sides shall use purchased profile linear guides with metal bearing blocks.
- Structural rolling bearings directly on square or round tube are not permitted.
- Each Y side shall use at least two bearing blocks with sufficient spacing to resist pitch, yaw, and gantry torsion.
- X shall use a rail/block arrangement stiff enough to resist Z-axis cantilever and torch-lead forces without carriage rocking.
- Exact guide size, preload, block style, and rail length shall be selected from verified manufacturer drawings or measurements.
- Rails and blocks shall be guarded from slag, abrasive dust, and water while remaining accessible for alignment and lubrication.

## 4. Ball-screw drive system

- X, Y-left, and Y-right shall use recirculating ball screws. ACME or trapezoidal main-axis screws are not permitted.
- Ball nuts shall be preloaded or otherwise verified to have sufficiently low backlash for the machine objective.
- Screw diameter and lead shall be selected separately for X and Y when that improves speed, moving mass, cost, or critical-speed margin.
- The longer X screw may be larger in diameter or higher in lead than the shorter Y screws.
- Candidate sizes shall include 16 mm and 20 mm nominal diameters with 10 mm or higher leads where appropriate.
- Every candidate shall be evaluated using actual root diameter, unsupported bearing span, support arrangement, motor speed, target cut speed, rapid speed, acceleration, torque, and nut speed limit.
- Fixed-fixed bearing support is preferred for maximum critical-speed margin when alignment and cost permit. Fixed-supported may be accepted only after calculation and testing.
- Screw guards shall protect ball tracks and nuts from plasma dust, water, and slag.
- Couplers, supports, motors, nuts, and lubrication points shall be serviceable without removing the water pan.

## 5. Motion performance

The final targets will be frozen after the plasma cut-speed range and mechanical envelope are verified, but the design shall prioritize:

- smooth contouring at thin-sheet cutting speeds;
- minimal measurable backlash and reversal error;
- high enough acceleration to preserve small-feature geometry;
- repeatable diagonal and circular interpolation;
- no lost position during direction changes or THC correction;
- stable motion at programmed velocity without screw whip or resonance;
- conservative operating speed below the selected screw manufacturer’s critical-speed recommendation.

Validation shall include:

- backlash and bidirectional repeatability tests;
- commanded-versus-measured travel calibration;
- circle, square, diagonal, and small-hole tests;
- full-speed dry contour tests;
- contour error testing through repeated reversals;
- live cutting tests in representative 16-gauge and 18-gauge material.

## 6. Motors and drives

- X, Y-left, Y-right, and Z require independent motor channels.
- Closed-loop NEMA 23/24 stepper systems are the value baseline.
- 400 W-class AC servos are the preferred no-compromise option if delivered cost and tuning complexity are acceptable.
- Open-loop plug-in stepper modules are not the preferred production drive for the precision machine.
- Motor and drive selection shall consider rotor inertia, screw inertia, desired acceleration, maximum RPM, supply voltage, encoder resolution, and fault reporting.
- Separate Y homing switches shall support automatic gantry squaring.

## 7. Z axis, floating touch-off, and breakaway

- Z shall use a compact precision linear guide and a ball screw or equivalent low-backlash powered drive.
- A floating touch-off head is mandatory.
- The floating mechanism shall provide repeatable switch travel, measurable offset, mechanical overtravel, and a normally closed industrial switch or equivalent fail-detecting input.
- A separate torch breakaway is required and shall stop motion/torch operation on activation.
- Ohmic sensing may be added as the primary probe, but the floating head shall remain as the mechanical fallback.
- Torch cable routing shall not lift or preload the floating slide anywhere in the work envelope.

## 8. Plasma control and operator interface

- The controller shall be selected by the complete precision-plasma requirements, not merely by hardware already on hand.
- The leading architecture is LinuxCNC with QtPlasmaC and deterministic Ethernet motion hardware.
- A FluidNC/Jackpot solution is acceptable only if controlled testing proves all required plasma functions without building a fragile parallel control stack.
- The normal operator interface shall provide homing, dual-Y squaring, jogging, work offsets, G-code preview, framing/perimeter trace, dry run, material profiles, probing, pierce/cut height, run/hold/resume/stop, cut recovery, alarms, and diagnostics.
- A generic G-code sender alone is not acceptable.

## 9. Plasma interface

- Torch start shall use verified isolated dry contacts.
- Arc OK shall enter through a verified isolated input.
- The Everlast divided-voltage output shall never connect directly to controller GPIO.
- DV polarity, divider ratio, loaded behavior, isolation, maximum expected output, scaling, and noise shall be verified before connection.
- The meter-induced voltage-reading change observed on the existing table shall be reproduced and explained before approving the X-1 voltage interface.
- No raw arc-voltage connection is permitted.

## 10. Torch height control

- Automatic closed-loop arc-voltage THC is mandatory for production release.
- THC movement shall remain position-aware and synchronized with the motion controller.
- Required functions include Arc OK gating, stabilization delay, target-voltage control, deadband or proportional correction law, correction-rate limits, Z travel limits, velocity/corner anti-dive, kerf/void behavior, cut-loss handling, and safe fault response.
- THC shall stop safely on E-stop, reset, Arc OK loss, signal loss, implausible voltage, probe conflict, limit activation, or controller fault.
- The operator shall be able to view live voltage, target voltage, THC enabled/active/inhibited state, anti-dive reason, correction state, and faults.
- Production release is blocked until THC is validated on representative warped thin sheet without torch dive or accumulated Z-position error.

## 11. Thin-sheet cut-quality controls

- The software stack shall support reduced-velocity treatment for small holes and arcs.
- Velocity anti-dive shall prevent THC from driving the torch downward during intentional deceleration, corners, holes, and tight contours.
- CAM and machine settings shall support lead-in control, overcut where appropriate, pierce-delay control, kerf compensation, and cut sequencing suitable for delicate signs.
- Cut-quality testing shall separate mechanical motion error, consumable condition, air quality, CAM strategy, torch timing, and THC behavior.

## 12. Safety and serviceability

- E-stop shall remove motion and torch-enable capability through hardware.
- Hardware safety shall not depend solely on a Windows or Linux application.
- The enclosure shall separate mains, motor power, controller, plasma interface, and low-level signals.
- Grounding, bonding, shielding, strain relief, ventilation, fire controls, and safe material handling are required.
- Every rail, block, nut, support, motor, switch, relay, and interface board shall be replaceable and documented.

## 13. Documentation and release gate

Rev B shall not be released until exact guides, blocks, ball screws, nuts, supports, motors, drives, Z components, and control hardware are selected from verified drawings or measurements.

Rev B must include:

- final support area, cut envelope, and overall dimensions;
- complete SolidWorks assembly and motion study;
- tube cut list and frame drawings;
- rail mounting and alignment details;
- carriage, motor, nut, support, Z, pan, slat, guard, and enclosure drawings;
- ball-screw critical-speed, torque, speed, acceleration, and resolution calculations;
- released DXFs and PDFs;
- mechanical/electrical BOM;
- wiring, grounding, and I/O diagrams;
- controller, operator-interface, probing, and THC configuration;
- alignment, calibration, and commissioning test records.

No unverified hole pattern, signal, or performance claim may be labeled released.
