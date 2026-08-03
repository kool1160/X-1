# Reference Material

The original reference files currently remain in the repository root so their filenames and history are preserved.

## X-1 Rev A plan

[`../X-1_CNC_Plasma_Table_Preliminary_Build_Plan_Rev_A.pdf`](../X-1_CNC_Plasma_Table_Preliminary_Build_Plan_Rev_A.pdf)

Purpose:

- records the initial X-1 concept;
- separates guide and drive functions;
- identifies tube-frame, linear-guide, metal-carriage, FluidNC, and staged-commissioning directions;
- defines the decisions required before Rev B.

This is a preliminary engineering plan, not a released manufacturing drawing set.

## CrossFire PRO MAX assembly guide

[`../CrossFire PRO MAX Assembly Guide _ Langmuir Systems.pdf`](../CrossFire%20PRO%20MAX%20Assembly%20Guide%20_%20Langmuir%20Systems.pdf)

Useful topics:

- dual-Y machine architecture;
- loose assembly followed by squaring and progressive tightening;
- rail/carriage alignment and preload;
- screw, nut, motor, and bearing-support arrangement;
- split water-pan assembly and sealing;
- slat installation;
- electronics-enclosure placement;
- service and safety considerations.

The X-1 does not inherit CrossFire dimensions or proprietary electronics from this guide.

## JD's Garage Imperial reference archive

[`../Imperial Version-20260802T230932Z-1-001.zip`](../Imperial%20Version-20260802T230932Z-1-001.zip)

The archive contains categories including:

- parts list;
- 3D-printed reference parts and jigs;
- tube and plate drawings;
- belt mounts, clamps, and tensioners;
- optional Z-axis and rotary-axis files;
- electronics/software support files;
- firmware and example G-code.

Useful X-1 lessons include the low-cost tube-frame approach, belt-drive packaging, gantry/torch proportions, and fabrication sequence. Structural printed parts are reference geometry only; the released X-1 design will use purchased linear blocks and metal structural carriages.

## Source-control rule

- Do not modify the original reference files.
- Put X-1-derived drawings and models in `cad/` and `drawings/`.
- State whether a dimension is source-derived, measured from a purchased component, or newly engineered for X-1.
- Verify third-party licensing and redistribution rights before any public release or redistribution of source material.
