# X-1 Design Requirements

## 1. Material capacity and work envelope

- The machine shall physically accept and support an untrimmed 48 × 48 inch half-sheet without cutting the stock down first.
- The nominal cutting-envelope target is approximately 48 × 48 inches.
- Exact usable X and Y travel shall be calculated from the selected standard-length guides and drive components.
- Material support is a hard requirement. Extra travel beyond the half-sheet target is not required unless it is gained at negligible cost and does not materially increase the footprint, shipping cost, screw-whip risk, or complexity.
- The existing large laser handles long work; X-1 shall not be enlarged to 4 × 5, 4 × 6, or 4 × 8 merely for additional length.
- The torch must reach the intended cut envelope without the trucks, ball nuts, belt clamps, rack pinions, cable chain, or limit targets reaching their physical limits.
- Provide intentional overtravel beyond software limits and hard stops that prevent a carriage from leaving its guides.

## 2. Structure

- Main structure shall use available 1/8-inch-wall steel tube wherever practical.
- The frame shall be welded and checked for diagonal equality, twist, and rail-pad straightness after cooling.
- Precision rails shall not be welded directly to the frame.
- Rail mounting surfaces shall be bolted, drilled/tapped, shimmed, or otherwise adjustable.
- Water, slat, and material loads shall not establish the precision alignment of the Y rails.
- Exterior skirts shall be removable and nonstructural.

## 3. Linear motion

- X and Y shall use purchased supported round rails or profile linear guides.
- Each Y side shall use at least two bearing blocks with useful spacing to resist pitch and yaw.
- X shall use enough rail/block spacing to resist torch-cable twist and Z-axis cantilever loads.
- Z shall use a metal linear guide or purchased slide.
- Structural 3D-printed bearing blocks are not permitted in the released design.
- Rails and blocks shall be protected from direct slag, abrasive plasma dust, and water splash.

## 4. Drive system

- Guides and drives are separate systems; linear rails do not provide propulsion.
- X/Y drive selection remains open among rack and pinion, timing belt, and ball screw.
- The chosen system must support independent Y-left and Y-right drive channels.
- Standard component lengths and replacement availability shall be considered before frame dimensions are frozen.
- The drive comparison shall prioritize the shortest standard components that still provide the required 48 × 48 sheet support and target cutting travel.
- Drive components shall be guarded while remaining accessible for tension, preload, lubrication, and replacement.
- The drive system shall not depend on a proprietary controller.

## 5. Controls

- Baseline controller is the V1 Engineering Jackpot CNC Controller V1.2.1.
- Baseline firmware is FluidNC or a controlled X-1 FluidNC fork required to meet locked machine requirements.
- X, Y-left, Y-right, and Z require independent motor channels.
- Separate left/right Y home switches shall support automatic gantry squaring.
- The configuration and any X-1 firmware changes shall be stored in this repository and backed up before machine changes.
- Any use of external step/direction drivers must be documented and electrically verified before connection.
- A controller migration is not permitted merely for convenience; it requires documented failure against a locked requirement and a decision-log update.

## 6. Operator software

- The finished machine shall have dedicated **X-1 operator software**. A generic G-code sender or the stock FluidNC WebUI alone is not an acceptable finished interface.
- FluidNC shall remain responsible for embedded motion control, stepping, homing, limits, probing inputs, real-time machine state, and any controller-side THC functions selected by the architecture.
- The operator application shall provide a plasma-specific workflow for machine setup, job preparation, execution, recovery, diagnostics, and maintenance.
- The application shall include machine connection status, homing, dual-Y squaring status, jogging, work offsets, G-code import, validation, preview, perimeter trace, dry run, job queue, run, pause, resume, stop, progress, alarms, and event logging.
- The application shall expose plasma-specific states including torch command, Arc OK, float/probe state, pierce sequence, cut height, limits, E-stop status, arc voltage, THC enabled/active state, target voltage, and THC faults.
- Jobs should be uploaded to and executed from controller storage when practical rather than depending on continuous Wi-Fi line streaming.
- The operator application shall preserve machine configuration, job history, material profiles, cut settings, and diagnostic logs locally.
- The application shall provide normal operator control of THC enable/disable and target setpoint after those interfaces are validated.
- Software shall never replace hardwired E-stop, torch inhibit, or other required safety circuits.

## 7. Plasma interface

- Torch start shall use verified isolated dry contacts.
- Arc OK shall enter the controller only through a verified isolated and correctly rated interface.
- The Everlast divided-voltage output shall never be connected directly to Jackpot or ESP32 GPIO.
- DV+ and DV- polarity, physical divider ratio, loaded behavior, and maximum expected output shall be verified before selecting the measurement interface.
- The unexplained voltage-display change caused by connecting the external meter shall be reproduced and resolved before the X-1 voltage interface is approved.
- Fixed-height cutting after probing shall be used as an intermediate commissioning baseline.

## 8. Torch height control

- The completed machine shall include automatic closed-loop arc-voltage THC.
- THC architecture selection is part of the current architecture phase and is not deferred to an unspecified future project.
- The selected architecture shall keep FluidNC's Z position synchronized with all THC movement.
- The voltage interface shall be galvanically isolated and protected against expected transients and plasma electrical noise.
- THC shall use Arc OK gating, stabilization delay, target-voltage control, correction limits, and a stable deadband or equivalent control method.
- THC shall include corner/velocity anti-dive and defined behavior for holes, lead-outs, kerf crossings, cut loss, implausible voltage, and sensor failure.
- THC correction shall stop safely on E-stop, reset, Arc OK loss, probe state conflict, limit activation, or controller fault.
- The operator shall be able to enable and disable THC and view live voltage, target voltage, active state, and fault state through X-1 Control.
- THC hardware, firmware, status protocol, configuration, and test results shall be stored in this repository.
- Production release is blocked until THC is validated on representative warped material without torch dive or accumulated Z-position error.

## 9. Safety

- Emergency stop shall remove torch-enable and motion capability through hardware, not software alone.
- The controller shall report E-stop state.
- Exposed motion areas shall be identified and guarded where practical.
- The electronics enclosure shall separate noisy/high-energy wiring from low-voltage signals.
- The machine shall provide grounding/bonding points, strain relief, cable protection, and service disconnects.
- Ventilation, fire protection, eye/skin protection, and safe material handling are required operating controls.

## 10. Serviceability

- No hidden loose nuts inside closed tube sections.
- Use rivnuts, weld nuts, tapped plates, studs, or accessible through-bolts.
- Motors, couplers, end supports, switches, and wiring terminations must be accessible without removing the water pan.
- Cosmetic skins must be removable in sections.
- Replaceable parts shall use documented hole patterns and part numbers.
- The isolated THC measurement interface and any co-processor shall be replaceable without disturbing the motion frame.

## 11. Documentation

Rev B shall not be released until actual guide and drive components are selected and the THC architecture boundary is defined. Rev B must include:

- final material-support area, work envelope, and overall dimensions;
- tube cut list;
- assembly model;
- laser-cut DXFs and fabrication drawings;
- rail/block and drive hole tables;
- motor and end-support drawings;
- wiring diagram and terminal schedule;
- FluidNC configuration and any X-1 firmware-fork definition;
- THC architecture, signal diagram, configuration, and validation plan;
- X-1 operator-software architecture and communication specification;
- alignment and commissioning checklist;
- released bill of materials.
