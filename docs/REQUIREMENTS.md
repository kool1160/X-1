# X-1 Design Requirements

## 1. Work envelope

- Must accept material at least 48 inches wide.
- Final Y travel must be calculated from the selected standard-length guide and drive components.
- Target Y cutting travel is approximately 60-72 inches.
- The torch must reach the full intended cut envelope without the trucks, ball nuts, belt clamps, rack pinions, cable chain, or limit targets reaching their physical limits.
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
- Drive components shall be guarded while remaining accessible for tension, preload, lubrication, and replacement.
- The drive system shall not depend on a proprietary controller.

## 5. Controls

- Baseline controller is the V1 Engineering Jackpot CNC Controller V1.2.1.
- Baseline firmware is FluidNC.
- X, Y-left, Y-right, and Z require independent motor channels.
- Separate left/right Y home switches shall support automatic gantry squaring.
- The configuration shall be stored in this repository and backed up before machine changes.
- Any use of external step/direction drivers must be documented and electrically verified before connection.

## 6. Operator software

- The finished machine shall have dedicated **X-1 operator software**. A generic G-code sender or the stock FluidNC WebUI alone is not an acceptable finished interface.
- FluidNC shall remain responsible for embedded motion control, stepping, homing, limits, probing inputs, and real-time machine state.
- The operator application shall provide a plasma-specific workflow for machine setup, job preparation, execution, recovery, diagnostics, and maintenance.
- The application shall include machine connection status, homing, dual-Y squaring status, jogging, work offsets, G-code import, validation, preview, perimeter trace, dry run, job queue, run, pause, resume, stop, progress, alarms, and event logging.
- The application shall expose plasma-specific states including torch command, Arc OK, float/probe state, pierce sequence, cut height, limits, and E-stop status.
- Jobs should be uploaded to and executed from controller storage when practical rather than depending on continuous Wi-Fi line streaming.
- The operator application shall preserve machine configuration, job history, material profiles, cut settings, and diagnostic logs locally.
- Future THC controls and voltage visualization shall be added only after the THC architecture and isolated voltage interface are verified.
- Software shall never replace hardwired E-stop, torch inhibit, or other required safety circuits.

## 7. Plasma interface

- Torch start shall use verified isolated dry contacts.
- Arc OK shall enter the controller only through a verified isolated and correctly rated interface.
- The Everlast divided-voltage output shall never be connected directly to Jackpot GPIO.
- The first operating release shall use fixed cut height after probing.
- THC shall be treated as a later design phase after the base machine is reliable.

## 8. Safety

- Emergency stop shall remove torch-enable and motion capability through hardware, not software alone.
- The controller shall report E-stop state.
- Exposed motion areas shall be identified and guarded where practical.
- The electronics enclosure shall separate noisy/high-energy wiring from low-voltage signals.
- The machine shall provide grounding/bonding points, strain relief, cable protection, and service disconnects.
- Ventilation, fire protection, eye/skin protection, and safe material handling are required operating controls.

## 9. Serviceability

- No hidden loose nuts inside closed tube sections.
- Use rivnuts, weld nuts, tapped plates, studs, or accessible through-bolts.
- Motors, couplers, end supports, switches, and wiring terminations must be accessible without removing the water pan.
- Cosmetic skins must be removable in sections.
- Replaceable parts shall use documented hole patterns and part numbers.

## 10. Documentation

Rev B shall not be released until actual guide and drive components are selected. Rev B must include:

- final work envelope and overall dimensions;
- tube cut list;
- assembly model;
- laser-cut DXFs and fabrication drawings;
- rail/block and drive hole tables;
- motor and end-support drawings;
- wiring diagram and terminal schedule;
- FluidNC configuration;
- X-1 operator-software architecture and communication specification;
- alignment and commissioning checklist;
- released bill of materials.
