# SPX4300 Precision Retrofit Evaluation

**Status:** Provisional study. No retrofit or new-build architecture is locked.

## Question

Would upgrading the existing large SPX4300-based plasma table produce more value than building a separate compact X-1 precision machine?

## Existing SPX4300 motion architecture from the supplied guides

The supplied SPX4300 gantry guide describes:

- two Y-axis rail tubes made from 2 x 4 inch rectangular tube, 14 AWG minimum through 12 AWG maximum;
- Y rail length equal to desired cut length plus 26 inches;
- published Y rail lengths of 121.93 inches for a 4 x 8 table and 145.93 inches for a 5 x 10 table;
- front and rear X gantry tubes made from 2 x 4 inch rectangular tube;
- straight 20-degree pressure-angle rack and pinion on X and both Y sides;
- direct-drive spur gears on three NEMA 23 motors;
- four 570 oz-in, 5 A NEMA 23 motors including Z;
- 48 V / 20 A motion power supply;
- rolling ball bearings and V-groove bearings running on structural tube or plate edges;
- a 12-inch, five-start ACME Z screw with anti-backlash nut;
- a floating-head touch-off switch.

The frame guide shows a large formed-sheet frame, sectional water pan, many cross supports, slat holders, and a structure that can be retained if inspection confirms it is square and sufficiently rigid.

## What can probably remain

Subject to measurement and inspection:

- main frame;
- legs and leveling system;
- water pan and slat bed;
- electrical enclosure shell;
- cable routing paths;
- torch source and machine torch;
- portions of the gantry structure if deflection testing is acceptable.

## What limits precision today

The current architecture can cut large work economically, but the likely precision limits are:

- bearings running on structural tubing rather than profile rails;
- carriage preload that depends on manual bearing adjustment;
- direct-drive straight rack and spur pinions without precision reduction;
- open-loop motors that cannot report following error;
- heavy twin-tube gantry and plate carriages;
- single-switch or manual gantry-squaring behavior;
- V-groove/plate-edge Z guidance and ACME Z drive;
- MyPlasm control and THC limitations.

Replacing only the motors will improve reliability and acceleration but will not remove guidance, pinion, Z, or control-system error.

## Provisional retrofit levels

### Level 1 - Drive and control refresh

Keep the tube rails, existing racks, carriages, and gantry.

Potential changes:

- closed-loop stepper or servo motors;
- independent left/right Y homing;
- improved spring-loaded pinion engagement;
- LinuxCNC/QtPlasmaC or another complete plasma controller;
- precision floating Z and closed-loop THC.

**Expected result:** noticeable improvement, lower lost-step risk, better THC and operator control. Not expected to reach the best contour quality because the tube-running guidance remains.

### Level 2 - Precision motion retrofit

Keep the frame, pan, and possibly the basic gantry envelope.

Potential changes:

- profile linear rails on both Y sides;
- profile rails on X;
- precision straight or helical rack with preloaded pinions;
- closed-loop servos or high-quality closed-loop steppers;
- independent Y homing and squaring;
- new low-backlash Z with floating head and breakaway;
- modern plasma controls and THC;
- rail and rack guards.

**Expected result:** the strongest value path if the frame is straight and the gantry can be made light enough. Large industrial laser and plasma machines commonly use rack drive on long axes; the problem is not rack itself, but rack quality, reduction, preload, guidance, control, and gantry mass.

### Level 3 - Frame-only reuse

Keep the SPX4300 frame, water system, and slats, but replace the entire moving bridge and control architecture.

Potential changes:

- new lightweight gantry;
- profile rails on X and Y;
- precision rack drive on all long axes;
- servo motion;
- new Z, touch-off, breakaway, controls, and THC.

**Expected result:** maximum full-table precision with the least compromise from the existing moving system. Highest retrofit cost and downtime, but still avoids building another frame and water table.

## Drive-system direction by axis

### Long Y axes

Do not assume ball screws. At 8 to 10 feet of travel, conventional rotating ball screws become expensive and difficult to run fast without critical-speed and whip problems.

The leading provisional options are:

1. helical rack and pinion with servo and planetary reduction;
2. quality straight rack with a properly preloaded or split-pinion system;
3. rotating-nut ball screw only if a detailed cost and speed study proves it worthwhile.

### X gantry axis

The X span is much shorter than Y. Both a ball screw and precision rack remain valid candidates.

A ball screw may provide excellent reversal behavior, but it adds screw inertia and must fit the actual gantry width. A precision rack may allow a lighter bridge and common drive components across X and Y.

### Z axis

Replace the existing five-start ACME and plate-edge guidance with:

- compact profile rails;
- small ball screw or another verified low-backlash drive;
- floating touch-off;
- separate torch breakaway;
- optional ohmic sensing;
- THC-compatible travel and acceleration.

## Upgrade-versus-new-build decision criteria

Before selecting either path, measure and compare:

- existing frame diagonal and twist;
- Y rail support straightness;
- gantry weight and measured deflection;
- carriage play and rack backlash;
- existing maximum acceleration without vibration;
- actual required table availability and acceptable downtime;
- delivered cost of rails, racks, servos, controls, Z, guards, and wiring;
- expected contour quality on 10 through 18 gauge;
- whether a smaller machine still offers a meaningful advantage after the large-table retrofit.

## Current engineering opinion

A full Level 2 or Level 3 retrofit may be a better investment than building a second machine because it could turn the existing large table into both the production table and the precision table.

However, a compact machine still has physical advantages for intricate work:

- shorter axes;
- lower moving mass;
- higher acceleration;
- easier contamination protection;
- easier alignment;
- no production downtime during development.

The next decision should therefore be based on measurements, not preference. No path is locked.
