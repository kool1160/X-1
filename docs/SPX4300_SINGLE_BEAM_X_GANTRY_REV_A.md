# SPX4300 4x8 Single-Beam X Gantry — Rev A

**Status:** Provisional build architecture. Nothing is locked unless Chris explicitly says `lock`.  
**Issue:** #20  
**Purpose:** Replace the binding dual-tube X bridge while preserving the existing Y system and expensive rack-and-pinion hardware.

## 1. Problem being removed

The existing X bridge uses two separate rectangular tubes and a front/rear carriage cage with rolling bearings contacting multiple tube faces. The physical carriage changes which bearings carry load as it travels. That creates position-dependent looseness, preload, binding, elastic windup, and release. It is not a tuning problem.

The replacement shall use:

- one structural beam;
- two purchased profile rails;
- one rigid X carriage plate;
- the existing rack, pinion, motor, cable chain, limit switch, and current Z during first commissioning;
- no custom milled or turned parts.

## 2. Existing-machine interface

The SPX4300 4x8 reference drawing lists both X gantry tubes at approximately **62.82 inches** long. The physical table and its existing Y carriage mounting interfaces override the drawing.

The new bridge shall bolt to the existing left and right Y carriages. Final end-plate DXFs are blocked until the physical bolt pattern and mounting span are measured.

## 3. Rev A architecture

### 3.1 Main beam

Preferred beam:

- rectangular steel tube;
- **6.00 inches vertical**;
- **4.00 inches deep** preferred;
- **6.00 inches deep** acceptable when free material is available and wall thickness is reasonable;
- approximately **0.120-inch / 11-gauge wall**;
- cut length based on the physical Y-carriage mounting span, with **62.82 inches used only as the reference starting dimension**.

The beam must be inspected before cutting for:

- vertical bow;
- horizontal bow;
- twist;
- dents;
- weld-seam placement;
- wall damage or corrosion.

#### Rough stiffness check

Assumptions:

- simply supported 62.82-inch steel beam;
- elastic modulus 29,000,000 psi;
- 35-pound centered moving load in addition to beam self-weight;
- 6x4x0.120 tube with the 6-inch dimension vertical.

Approximate results:

- beam weight: 41.6 pounds;
- calculated vertical deflection from self-weight plus centered 35-pound load: about 0.001 inch.

This is an envelope check, not a released structural analysis. Actual wall thickness, beam condition, end restraint, rail bars, carriage mass, and dynamic loading must be entered before release.

### 3.2 End interfaces

Use two laser-cut **1/4-inch steel end plates**.

Each end plate shall:

- locate against the end of the single beam;
- include tab-and-slot features for repeatable beam location;
- use short, balanced TIG welds at the beam ends only;
- include slotted mounting holes matching the existing Y carriage interface;
- provide vertical and fore/aft adjustment during squaring;
- include a positive mechanical shoulder so carriage bolts do not carry the entire vertical load by friction alone;
- include hard-stop and home-switch flag provisions.

Do not weld long seams along the beam faces after rail alignment.

### 3.3 Rail foundations

Do not assume the face of structural tube is a precision rail surface.

Use two separate rail foundation bars:

- **1/4 x 2-inch cold-finished steel flat bar**;
- approximately 60 inches long;
- one upper bar and one lower bar on the front face;
- nominal vertical rail centerline separation: **4.00 inches**.

Each foundation bar shall have:

- clearance slots for attachment to the beam at roughly 8–10-inch intervals;
- small jack-screw holes between attachment points;
- tapped holes matching the selected rail's actual manufacturer drawing;
- end reference marks and measurement datums.

Use internal nut strips or backing strips inside the open beam before the end plates are installed. The rail bars are aligned straight and coplanar, then the purchased rails are mounted to them.

Do not cut final rail-hole patterns from a generic HGR drawing. Select the exact rail and block package first and use its supplied drawing or the measured hardware.

### 3.4 Linear guidance

Rev A candidate:

- two nominal **20 mm profile rails**;
- nominal rail length: **1500 mm**;
- two blocks per rail;
- four blocks total;
- upper and lower rails on the front face;
- block spacing on each rail: approximately 6 inches center-to-center, subject to the current Z envelope and torch offset.

A 1500 mm rail leaves end space on the approximately 62.82-inch beam while still supporting the required 48-inch cutting travel.

The exact rail series, block style, preload, mounting screws, lubrication fittings, and wipers remain open until a purchase candidate is selected.

### 3.5 X carriage

Use one laser-cut **1/4-inch steel carriage plate**.

Nominal starting envelope:

- 12 inches wide;
- 10 inches tall;
- clearance holes for the four purchased rail blocks;
- slotted adapter pattern for the current Z assembly;
- separate mounting holes for the motor-pivot bracket;
- cable-chain attachment;
- home-switch target;
- future breakaway and replacement-Z provisions.

The carriage plate shall be flat. It shall not be formed into a box that forces four blocks into alignment. Spacer stand-offs, if required, shall be purchased precision spacers or stacked shim packs rather than custom turned parts.

### 3.6 Rack carrier and rack reuse

Reuse the existing X gear rack.

Mount it to a removable carrier rather than permanently welding it to the new main beam.

Candidate carrier:

- 1/8-inch or 11-gauge laser-formed angle/channel, or purchased steel angle;
- slotted bolt holes at roughly 8–12-inch intervals;
- rack attached with the same small spaced TIG-tack approach already proven by the owner;
- teeth facing downward to reduce direct plasma debris accumulation;
- carrier adjusted parallel to the master rail before final tightening.

Removal from the old beam shall preserve the rack teeth and reference edge. The rack must be checked against a straightedge after removal.

### 3.7 Pinion and motor mount

Reuse the existing motor and pinion for Rev A testing unless inspection rejects them.

Use a laser-cut **1/4-inch pivoting motor plate** with:

- the existing NEMA motor pattern;
- a purchased shoulder bolt or hardened pivot bolt;
- purchased flanged bronze bushings or purchased bearing pivot hardware;
- two tension springs or one equivalent spring mechanism;
- an adjustable positive stop that establishes maximum pinion depth;
- a manual release feature for carriage testing and service;
- provision for a future belt-reduction plate without replacing the carriage.

The springs maintain mesh. They do not force the pinion deeply into the rack. The hard stop sets depth; the spring only maintains contact.

### 3.8 Current Z reuse

The first version shall reuse the current powered Z and floating torch assembly through a laser-cut adapter plate.

This isolates the X-guidance repair from a simultaneous Z redesign. After the new X axis passes pen and fixed-height tests, the current Z may be replaced with a compact profile-rail Z, floating touch-off, breakaway, and revised torch holder.

The adapter plate shall preserve:

- torch centerline within current usable X/Y travel;
- existing touch-off travel;
- existing motor and screw alignment;
- access to consumables;
- current limit-switch function.

## 4. Fabricated parts

All provisional until physical measurements are entered.

| ID | Part | Qty | Material/process |
|---|---|---:|---|
| GX-001 | Main single beam | 1 | 6-inch-tall rectangular steel tube, approximately 11 ga |
| GX-002 | Left end plate | 1 | 1/4-inch steel, laser cut, TIG welded |
| GX-003 | Right end plate | 1 | 1/4-inch steel, laser cut, TIG welded |
| GX-004 | Upper rail foundation bar | 1 | 1/4 x 2 cold-finished flat bar, drilled/tapped |
| GX-005 | Lower rail foundation bar | 1 | 1/4 x 2 cold-finished flat bar, drilled/tapped |
| GX-006 | Upper internal nut strip | 1 | 3/16 or 1/4-inch steel, laser cut and tapped |
| GX-007 | Lower internal nut strip | 1 | 3/16 or 1/4-inch steel, laser cut and tapped |
| GX-008 | X carriage plate | 1 | 1/4-inch steel, laser cut |
| GX-009 | X motor pivot plate | 1 | 1/4-inch steel, laser cut |
| GX-010 | Rack carrier | 1 | 1/8-inch or 11-ga formed steel / purchased angle |
| GX-011 | Current-Z adapter plate | 1 | 1/4-inch steel, laser cut |
| GX-012 | Cable-chain bracket | 1 | 11-ga formed steel |
| GX-013 | Home-switch flag/bracket | 1 set | 1/8-inch steel |

## 5. Purchased precision parts

| Item | Qty | Requirement |
|---|---:|---|
| Profile rails | 2 | Nominal 20 mm, nominal 1500 mm; exact series open |
| Matching blocks | 4 | Two per rail; exact block style open |
| Pivot shoulder bolt | 1 | Sized after motor plate layout |
| Pivot bushings/bearings | 1 set | Purchased standard parts |
| Tension springs | 2 | Selected after motor/pinion geometry |
| Rail and block hardware | 1 set | Exact manufacturer-specified grade and length |
| Alignment shims | as required | Stainless shim stock |
| Rack-carrier fasteners | as required | Grade 8 or property-class equivalent |

## 6. Reused parts

- existing X gear rack;
- existing X pinion;
- existing X motor for initial tests;
- existing X cable chain where length and bend radius remain suitable;
- existing X home/limit switch where serviceable;
- existing powered Z and floating torch head for initial commissioning;
- existing Y carriages, Y racks, Y motors, frame, pan, and slat bed.

## 7. Required field measurements

Record all measurements in inches and photograph each datum.

1. Distance between the left and right Y carriage mounting datums.
2. Existing X tube cut length and overall installed bridge width.
3. Mounting-bolt coordinates on both Y carriage top plates.
4. Height of the current X beam centerline above the slats.
5. Front/rear clearance available for a 4-inch-deep and 6-inch-deep beam.
6. Existing X rack length, base width, base thickness, tooth orientation, and joint locations.
7. Existing pinion tooth count, pitch diameter if known, bore, key/set-screw condition, and motor shaft diameter.
8. X motor model, frame size, current, and shaft length.
9. Current Z assembly mounting-hole coordinates and overall moving envelope.
10. Torch centerline offset from the current rear X tube and from the Y carriage centerline.
11. Candidate beam outside size, wall thickness, measured weight, and straightness in both planes.

## 8. Build and validation sequence

1. Measure and model the physical Y carriage interface.
2. Select and inspect the candidate single beam.
3. Select the exact rail/block package and import its actual drawing.
4. Release rail bars, internal nut strips, and a temporary test carriage.
5. Align rail bars on the beam without the rack, motor, or Z.
6. Install rails and blocks; verify free carriage movement by hand.
7. Release and install the final carriage plate.
8. Remove and inspect the existing rack and pinion.
9. Build the removable rack carrier and spring-loaded pinion mount.
10. Install current Z through the adapter plate.
11. Mount the bridge to the existing Y carriages and square it.
12. Run motor-off pull-force and indicator tests.
13. Run motor-on dry motion at reduced acceleration.
14. Run pen tests: squares, diagonals, 4-inch circles, and 8-inch circles at left, center, and right.
15. Run fixed-height plasma coupons only after pen geometry is repeatable.
16. Proceed to controller/THC and replacement-Z work only after the X mechanics pass.

## 9. Rev A acceptance targets

Provisional targets to be reviewed after measurement capability is confirmed:

- no changing block contact or detectable carriage rock across full X travel;
- hand-pull force variation no greater than approximately ±20 percent after seals and lubrication settle;
- rail foundation straightness within 0.005 inch over the working length;
- upper/lower rail separation variation within 0.003 inch over working travel;
- rack-to-master-rail parallelism within 0.005 inch over working travel;
- no pinion tight spot through the full rack length;
- commanded 4-inch and 8-inch pen circles repeat at left, center, and right without location-dependent flattening or ovality;
- no released component requires custom milling or turning.

## 10. Explicit non-goals for Rev A

- no router spindle capability;
- no second X beam;
- no rolling bearings directly on tube;
- no new X ball screw;
- no replacement of the expensive rack/pinion without inspection evidence;
- no simultaneous full Z redesign;
- no final controller or THC selection in this mechanical release;
- no final DXFs until physical dimensions and exact purchased rails are entered.
