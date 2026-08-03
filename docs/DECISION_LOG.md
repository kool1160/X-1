# X-1 Decision Log

This file records project decisions separately from brainstorming. A decision is not considered locked until it appears here.

## Locked decisions

### D-001 - Project identity

- **Decision:** Name the machine **X-1 - Laser X Design 1**.
- **Status:** Locked
- **Date:** 2026-08-02

### D-002 - Primary fabrication method

- **Decision:** Use available 1/8-inch-wall steel tube and laser-cut/formable metal parts for the structure, pan, brackets, guards, carriages, and enclosure.
- **Status:** Locked
- **Date:** 2026-08-02

### D-003 - Sheet-metal role

- **Decision:** Use laser-cut/formable sheet metal for carriages, brackets, mounts, gussets, guards, one-piece water pan, enclosure, slat holders, and removable cosmetic panels.
- **Status:** Locked
- **Date:** 2026-08-02

### D-004 - Purchased profile-rail direction

- **Original decision:** Use purchased profile or supported-round linear guides.
- **Status:** Restored and superseded by **D-016** with profile rails selected for the precision machine.
- **Date:** 2026-08-02

### D-005 - Controller and firmware

- **Original decision:** Use the V1 Engineering Jackpot CNC Controller with FluidNC.
- **Status:** Open for re-evaluation under **D-017** because the finished machine requires mature plasma-specific motion, probing, THC, anti-dive, and recovery.
- **Date:** 2026-08-02

### D-006 - Dual-Y architecture

- **Decision:** Use independent left and right Y motors and drive screws, with independent homing/squaring.
- **Status:** Locked
- **Date:** 2026-08-02

### D-007 - Staged cutting commissioning

- **Decision:** Commission motion, probing, isolated torch control, Arc OK, and fixed-height cutting before enabling automatic Z correction.
- **Clarification:** Fixed-height cutting is an intermediate validation step, not the finished machine capability.
- **Status:** Locked
- **Date:** 2026-08-02

### D-008 - Material capacity and compact format

- **Decision:** X-1 shall remain a compact half-sheet machine. The one-piece water/slat bed must accept the intended half-sheet stock with practical loading clearance; exact cut travel is set by the precision-motion geometry.
- **Status:** Locked requirement; final envelope open until CAD closes
- **Date:** 2026-08-02

### D-009 - Dedicated operator software

- **Decision:** The finished machine shall have a complete plasma-machine operator interface. A generic sender alone is not acceptable.
- **Clarification:** A mature existing plasma interface such as QtPlasmaC may satisfy this requirement; custom X-1 software remains optional only where it adds real value rather than duplicating proven machine functions.
- **Status:** Requirement locked; implementation open
- **Date:** 2026-08-02

### D-010 - Automatic THC is required

- **Decision:** The completed X-1 must include automatic closed-loop torch-height control based on isolated arc-voltage measurement.
- **Required behavior:** Touch-off/floating-head probing, Arc OK gating, stabilization delay, velocity/corner anti-dive, fault handling, live voltage/status, and no accumulated Z-position error.
- **Status:** Locked
- **Date:** 2026-08-02

### D-011 - Controlled scope

- **Decision:** Only work listed in `PROJECT_STATUS.md` is active. Unrelated ideas stay in `PARKING_LOT.md` until formally approved.
- **Status:** Locked
- **Date:** 2026-08-02

### D-012 - 16 mm ball-screw direction

- **Original decision:** Use 16 mm ball screws on X and both Y axes.
- **Status:** Superseded by **D-016**. Exact diameter and lead must be selected from speed, acceleration, critical-speed, weight, and cost calculations rather than a diameter guess.
- **Date:** 2026-08-02

### D-013 - CrossFire PRO mechanical replica

- **Original decision:** Reproduce the standard CrossFire PRO frame and motion system as faithfully as possible.
- **Status:** **Superseded by D-015.** The CrossFire PRO guide remains a reference for packaging, one-piece/compact table proportions, dual-Y layout, assembly sequence, water/slat concepts, and floating-head function. It is not the final motion architecture.
- **Date:** 2026-08-03

### D-014 - CrossFire PRO ACME main-axis drive

- **Original decision:** Use OEM-equivalent multi-start ACME screws and acetal anti-backlash nuts.
- **Status:** **Superseded by D-016.** ACME screws are not acceptable for the precision-sign-cutter objective.
- **Date:** 2026-08-03

### D-015 - Precision sign-cutter mission

- **Decision:** X-1 is a compact, high-quality CNC plasma machine optimized for intricate 16-gauge and 18-gauge signs and delicate profiles, not a low-cost CrossFire clone and not a replacement for the existing large plasma table.
- **Priority order:** contour fidelity, low backlash, smooth direction reversal, small-feature quality, acceleration, repeatable touch-off, stable THC, serviceability, and then maximum cutting envelope.
- **Reference boundary:** CrossFire PRO geometry and assembly concepts may be reused only where they do not compromise precision motion.
- **Status:** Locked
- **Date:** 2026-08-03

### D-016 - Precision linear motion

- **Decision:** Use profile linear rails with metal carriages on X and both Y sides. Use recirculating ball screws on X, Y-left, and Y-right. No ACME screws and no structural rolling bearings running directly on tube.
- **Ball-screw requirements:** preloaded or low-backlash nuts; verified root diameter; verified lead; speed and critical-speed calculation; supported at both ends; fixed-fixed support preferred where alignment and cost permit; guarded from plasma dust and water.
- **Sizing direction:** evaluate 16 mm and 20 mm screws with 10 mm or higher lead as appropriate. The longest X screw may require a larger diameter or higher lead than the shorter Y screws. Exact selections remain open until the machine envelope and motion targets are calculated.
- **Guidance direction:** profile rails are preferred over SBR supported round rails for rigidity, compact carriage geometry, and repeatability. Exact HGR/HGW size and block count remain open.
- **Status:** Architecture locked; exact components open
- **Date:** 2026-08-03

### D-017 - Plasma-control platform selection

- **Decision:** Select the controller by the precision-plasma requirements rather than by already-owned hardware.
- **Current leading architecture:** LinuxCNC + QtPlasmaC with deterministic Ethernet motion hardware and an isolated arc-voltage interface.
- **FluidNC/Jackpot rule:** FluidNC may remain only if bench testing proves position-aware THC, velocity anti-dive, floating-head probing, dual-Y squaring, cut recovery, and the required operator workflow without building an entire plasma-control stack from scratch.
- **Status:** Decision gate open; LinuxCNC/QtPlasmaC is preferred
- **Date:** 2026-08-03

### D-018 - One-piece water bed and floating head

- **Decision:** Use a one-piece welded water pan integrated into or supported by the frame, with welding sequence and isolation designed so pan distortion does not alter rail alignment. Use a powered Z slide with a floating touch-off head and a separate torch breakaway.
- **Status:** Locked
- **Date:** 2026-08-03

## Open decisions

### O-001 - Final work envelope and frame geometry

- clear sheet-support dimensions
- actual X/Y cutting travel
- overall footprint and access space
- one-piece pan depth, drains, and slat layout
- rail mounting surfaces and alignment adjustment

### O-002 - Profile rails

- Y rail size, length, preload class, and two-block spacing per side
- X rail arrangement: one HGR20, dual HGR15, or equivalent
- Z guide size and floating-head arrangement
- rail protection and lubrication access

### O-003 - Ball-screw packages

- exact X and Y screw diameters, leads, lengths, and root diameters
- fixed-supported versus fixed-fixed supports
- single preloaded nut versus double nut
- end machining, bearing blocks, couplers, and motor interfaces
- critical-speed, rapid-speed, acceleration, and torque calculations

### O-004 - Motors and drives

- closed-loop NEMA 23/24 stepper system versus 400 W-class AC servos
- motor inertia, encoder resolution, drive voltage, and tuning
- direct coupling versus timing-belt reduction

### O-005 - Z axis and sensing

- compact ball screw or precision lead mechanism
- powered travel and floating travel
- touch-off switch, overtravel, and breakaway design
- ohmic sensing as optional primary probe with float fallback

### O-006 - Control platform

- LinuxCNC/QtPlasmaC + Mesa-class Ethernet hardware + isolated voltage interface
- FluidNC/Jackpot only after documented requirement testing
- exact I/O count, step/dir channels, Arc OK, torch relay, E-stop, probing, and THC input hardware

### O-007 - Operator software

- QtPlasmaC as the production operator interface
- optional X-1 companion application only for functions not already handled well by QtPlasmaC

## Change rule

A locked decision can be changed when new measurements, source evidence, cost, safety, or testing justify it. Preserve the old entry and record the replacement decision rather than silently rewriting history.
