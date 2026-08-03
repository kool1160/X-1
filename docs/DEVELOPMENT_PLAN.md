# X-1 Development Plan

## Phase 0 - Reference and requirements

- Preserve the original reference files.
- Separate source-derived observations from X-1 engineering decisions.
- Maintain requirements and decision logs.
- Do not release manufacturing drawings from nominal online dimensions.

**Exit condition:** project requirements and open decisions are documented.

## Phase 1 - Component selection

Select actual purchasable components for:

- Y guides and blocks;
- X guides and blocks;
- X/Y drive system;
- motors and drivers;
- Z guide and drive;
- cable chain;
- home/probe switches;
- torch relay and input isolation.

Record delivered cost, exact dimensions, listing/model, replacement availability, and datasheets.

**Exit condition:** every dimension-critical component has an exact model and drawing or verified measurement.

## Phase 2 - Rev B engineering release

Create:

- complete SolidWorks assembly;
- final work envelope and overall size;
- tube cut list;
- Y truck and gantry end-plate drawings;
- X carriage and Z drawings;
- motor, nut, rack, pulley, bearing, or end-support mounts;
- rail drilling/slot tables;
- water-pan and slat drawings;
- removable skirt drawings;
- released BOM;
- preliminary wiring diagram;
- FluidNC I/O map.

**Exit condition:** no critical hole pattern remains based on a generic product picture.

## Phase 3 - Frame and pan fabrication

1. Cut and deburr tube.
2. Fixture and tack the main frame.
3. Equalize diagonals and control twist.
4. Weld with a balanced sequence.
5. Allow full cooling and remeasure.
6. Add adjustable/bolt-on rail mounting surfaces.
7. Fabricate the separate pan/slat support system.
8. Fabricate removable water pan, drains, slat combs, and slats.

**Hold point HP-1:** frame has no rock, diagonals are documented, and rail pads can be aligned straight.

## Phase 4 - Mechanical motion assembly

1. Establish one Y rail as the master.
2. Install both Y trucks.
3. Float and align the second Y rail by moving the gantry through full travel.
4. Build and install the gantry without forcing the trucks out of alignment.
5. Install X guide(s), drive, carriage, and cable chain.
6. Install Z guide, drive, probe mechanism, and torch mount.
7. Add hard stops and removable rail/drive guards.

**Hold point HP-2:** X/Y/Z move through full travel with consistent force and no truck rocking or binding.

## Phase 5 - Electrical bench build

- Build the enclosure with separated power, motor, control, and plasma-interface zones.
- Power and test the Jackpot without the plasma cutter connected.
- Test each motor channel individually.
- Test every switch and E-stop status input by hand.
- Test the torch relay as dry contacts only.
- Verify power-supply polarity, voltage, driver current, grounding, and cable shielding.

**Hold point HP-3:** E-stop removes motion/torch capability and every I/O point is documented.

## Phase 6 - FluidNC commissioning

- Create and commit the first machine configuration.
- Verify axis directions at low current/speed.
- Home X, Z, Y-left, and Y-right.
- Verify repeatable gantry squaring.
- Calibrate commanded travel against measured travel.
- Tune conservative velocity and acceleration.
- Run dry G-code over the full work envelope.

**Hold point HP-4:** repeated power cycles and homing produce stable square and position.

## Phase 7 - Plasma commissioning

1. Connect isolated torch start.
2. Verify torch ON/OFF with motion disabled.
3. Verify Arc OK only through a proven isolated interface if used.
4. Establish probing and pierce-height behavior.
5. Cut fixed-height straight lines.
6. Cut squares and circles.
7. Separate CAM lead-in/lead-out problems from machine-control problems.
8. Record consumables, amperage, air pressure, feed, pierce delay, and results.

**Hold point HP-5:** basic profiles cut reliably without THC.

## Phase 8 - THC development

Only begin after HP-5. Evaluate:

- standalone THC controlling Z up/down;
- isolated voltage measurement feeding custom FluidNC development;
- migration to a controller/software stack with mature integrated THC.

The Everlast divided-voltage output shall not be connected to Jackpot GPIO directly.

## Phase 9 - Finish and release

- Fit cosmetic skirts and branded panels.
- Complete guards and service labels.
- Update as-built CAD and wiring.
- Publish Rev C as-built documents.
- Archive released FluidNC configuration and calibration data.
