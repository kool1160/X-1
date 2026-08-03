# X-1 Decision Log

This file records project decisions separately from brainstorming. A decision is not considered locked until it appears here.

## Locked decisions

### D-001 - Project identity

- **Decision:** Name the machine **X-1 - Laser X Design 1**.
- **Status:** Locked
- **Date:** 2026-08-02

### D-002 - Primary fabrication method

- **Decision:** Use available 1/8-inch-wall steel tube and laser-cut/formable metal parts to reproduce the selected frame and motion architecture.
- **Status:** Locked
- **Date:** 2026-08-02

### D-003 - Sheet-metal role

- **Decision:** Use laser-cut/formable sheet metal for carriages, brackets, mounts, gussets, guards, water pan, enclosure, slat holders, and removable cosmetic panels.
- **Status:** Locked
- **Date:** 2026-08-02

### D-004 - Purchased profile-rail direction

- **Original decision:** Use purchased profile or supported-round linear guides.
- **Status:** **Superseded by D-013.** X-1 now copies the CrossFire PRO tube-rail and adjustable rolling-bearing carriage architecture.
- **Date:** 2026-08-02

### D-005 - Controller and firmware

- **Decision:** Use the V1 Engineering Jackpot CNC Controller V1.2.1 with FluidNC or a controlled X-1 FluidNC fork.
- **Status:** Locked
- **Date:** 2026-08-02

### D-006 - Dual-Y architecture

- **Decision:** Use independent left and right Y motors and drive screws.
- **Status:** Locked
- **Date:** 2026-08-02

### D-007 - Staged cutting commissioning

- **Decision:** Commission motion, probing, isolated torch control, Arc OK, and fixed-height cutting before enabling automatic Z correction.
- **Clarification:** Fixed-height cutting is an intermediate validation step, not the finished machine capability.
- **Status:** Locked
- **Date:** 2026-08-02

### D-008 - 50 × 50 custom half-sheet bed

- **Original decision:** Create approximately 50 × 50 inches of clear support area.
- **Status:** **Superseded by D-013.** The standard CrossFire PRO mechanical envelope is now the replica target.
- **Date:** 2026-08-02

### D-009 - Dedicated operator software

- **Decision:** Build dedicated X-1 operator software. The finished machine will not rely on a generic G-code sender or FireControl.
- **Architecture:** FluidNC owns embedded motion; X-1 Control owns the plasma-specific operator workflow, job system, visualization, diagnostics, material profiles, alarms, recovery, and THC interface.
- **Status:** Locked
- **Date:** 2026-08-02

### D-010 - Automatic THC is required

- **Decision:** The completed X-1 must include automatic closed-loop torch-height control based on isolated arc-voltage measurement.
- **Status:** Requirement locked; exact implementation open
- **Date:** 2026-08-02

### D-011 - Controlled scope

- **Decision:** Only work listed in `PROJECT_STATUS.md` is active. Unrelated ideas stay in `PARKING_LOT.md` until formally approved.
- **Status:** Locked
- **Date:** 2026-08-02

### D-012 - 16 mm ball-screw direction

- **Original decision:** Use 16 mm ball screws on X and both Y axes.
- **Status:** **Superseded by D-014.** The replica uses CrossFire PRO multi-start ACME lead screws.
- **Date:** 2026-08-02

### D-013 - CrossFire PRO mechanical replica

- **Decision:** Reproduce the standard Langmuir CrossFire PRO frame and motion system as faithfully as source dimensions and verified measurements allow.
- **Mechanical authority:** Standard CrossFire PRO assembly guide and published PRO specifications, not the PRO MAX.
- **Copy:** frame, legs, lower rails, Y tube rails, stanchions, adjustable rolling carriages, gantry, X carriage, ACME drive, couplers, bearings, NEMA 23 motors, water tray, slats, powered floating Z, and IHS mechanism.
- **Do not copy:** Langmuir electronics, controller, FireControl, computer/touchscreen, wiring enclosure internals, or LS-THC.
- **Published target:** 48.25 in X × 33.3 in Y cutting envelope and approximately 54.2 in × 69.5 in floor space.
- **Accuracy rule:** The assembly guide is not a manufacturing drawing package. Hidden critical dimensions must be verified before release; unverified geometry must be labeled inferred.
- **Status:** Locked
- **Date:** 2026-08-03

### D-014 - CrossFire PRO ACME main-axis drive

- **Decision:** Use OEM-equivalent multi-start ACME lead screws and acetal anti-backlash nuts.
- **Y-left and Y-right:** 3/8-8, 4-start ACME.
- **X:** 1/2-10, 5-start ACME.
- **Common advance:** 0.5 inch per revolution.
- **Support:** 608 bearing at the non-motor end; clamping coupler to NEMA 23 motor at the drive end.
- **Motor baseline:** X and both Y motors at 284 oz-in NEMA 23; Z at 180 oz-in NEMA 23.
- **Status:** Locked specification; exact lengths and end-machining dimensions must be reconstructed
- **Date:** 2026-08-03

## Open decisions

### O-001 - Exact frame manufacturing geometry

- tube section dimensions and cut lengths
- hole locations and tube spacers
- stanchion plate dimensions
- leg height and leveling-foot details
- gusset and skirt geometry

### O-002 - Tube rail and carriage geometry

- Y rail lengths, hole pattern, and coating
- bearing size, spacing, eccentric/preload details
- X gantry tube and carriage geometry
- exact truck overhang and hard-stop positions

### O-003 - ACME screw purchase package

- exact overall lengths
- turned journal diameters and lengths
- tapped end details
- coupler bores
- anti-backlash-nut mounting pattern
- motor and bearing mount dimensions

### O-004 - Z-axis reconstruction

- guide geometry and powered stroke
- floating travel and switch mechanism
- torch mount dimensions
- screw and nut specification

### O-005 - Required THC architecture

- integrated X-1 FluidNC THC module
- dedicated co-processor with position-aware FluidNC interface
- standalone external THC only if Z-position reconciliation is proven
- controller migration only if FluidNC fails a locked requirement

### O-006 - Operator-software implementation

- Tauri/React/TypeScript desktop application
- native .NET desktop application
- another offline Windows architecture proven through a communication prototype

## Change rule

A locked decision can be changed when new measurements, source evidence, cost, safety, or testing justify it. Preserve the old entry and record the replacement decision rather than silently rewriting history.
