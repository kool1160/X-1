# X-1 Decision Log

This file records project decisions separately from brainstorming. A decision is not considered locked until it appears here.

## Locked decisions

### D-001 - Project identity

- **Decision:** Name the machine **X-1 - Laser X Design 1**.
- **Status:** Locked
- **Date:** 2026-08-02

### D-002 - Primary structure

- **Decision:** Use available 1/8-inch-wall steel tube for the main welded frame and gantry where appropriate.
- **Reason:** Material is available at no cost, tube is fast to fabricate, and a tube structure avoids unnecessary formed-part count and hardware.
- **Status:** Locked
- **Date:** 2026-08-02

### D-003 - Sheet-metal role

- **Decision:** Use laser-cut/formable sheet metal for carriages, brackets, guards, water pan, enclosure, slat holders, and removable cosmetic skirts. Do not make the entire structural frame a folded-sheet assembly.
- **Status:** Locked
- **Date:** 2026-08-02

### D-004 - Guide-system direction

- **Decision:** Use purchased linear guides and metal structural carriages on X and Y instead of structural 3D-printed bearing assemblies.
- **Open detail:** Supported round rail versus profile rail and final sizes.
- **Status:** Direction locked; component selection open
- **Date:** 2026-08-02

### D-005 - Controller and firmware

- **Decision:** Use the existing V1 Engineering Jackpot CNC Controller V1.2.1 with FluidNC for the first X-1 control system.
- **Status:** Locked for prototype
- **Date:** 2026-08-02

### D-006 - Dual-Y architecture

- **Decision:** Use independent left and right Y motors with separate home switches for automatic gantry squaring.
- **Status:** Locked
- **Date:** 2026-08-02

### D-007 - Staged cutting commissioning

- **Decision:** Commission motion, probing, isolated torch control, Arc OK, and fixed-height cutting before enabling automatic Z correction.
- **Clarification:** This is a troubleshooting and validation sequence. Fixed-height cutting is not the final X-1 capability and does not remove THC from the active project scope.
- **Status:** Locked
- **Date:** 2026-08-02

### D-008 - Machine length

- **Decision:** Do not force a nominal 4 x 8 or 4 x 6 size before component selection. Final Y travel will be based on the best-value standard guide and drive lengths.
- **Target:** Approximately 60-72 inches of usable Y travel.
- **Status:** Locked approach; final dimension open
- **Date:** 2026-08-02

### D-009 - Dedicated operator software

- **Decision:** Build dedicated X-1 operator software. The finished machine will not rely on a generic G-code sender or the stock FluidNC WebUI as its primary operating interface.
- **Architecture:** FluidNC remains the embedded motion-control firmware. The X-1 application provides the plasma-specific operator workflow, job management, visualization, diagnostics, material profiles, alarms, recovery, and THC interface.
- **Job execution direction:** Prefer uploading jobs to controller storage and starting them from FluidNC storage rather than depending on continuous Wi-Fi G-code streaming.
- **Status:** Locked
- **Date:** 2026-08-02

### D-010 - Automatic THC is required

- **Decision:** The completed X-1 must include automatic closed-loop torch-height control based on isolated arc-voltage measurement.
- **Required behavior:** Position-aware Z correction, Arc OK gating, delay, anti-dive, fault handling, operator enable/disable, voltage/status display, and no accumulated Z-position error.
- **Open detail:** Exact FluidNC-compatible hardware and firmware architecture.
- **Status:** Requirement locked; architecture open
- **Date:** 2026-08-02

### D-011 - Single active phase and controlled scope

- **Decision:** Only work listed in `PROJECT_STATUS.md` is active. Unrelated ideas are recorded in `PARKING_LOT.md` and do not change the baseline without a formal decision update.
- **Status:** Locked
- **Date:** 2026-08-02

## Open decisions

### O-001 - Y linear guide

- SBR20 supported round rail
- HGR20 profile rail
- Other only with documented load, price, and mounting advantage

### O-002 - X linear guide

- SBR16/SBR20
- Dual HGR15
- HGR20

### O-003 - X/Y drive system

- Rack and pinion
- Timing belt
- Ball screw

### O-004 - Motors and drives

- Onboard TMC2209 modules
- Existing external drives
- New DM542/DM556-class external drives

### O-005 - Z assembly

- Fabricated metal Z slide
- Purchased compact linear Z assembly

### O-006 - Required THC architecture

- Integrated X-1 FluidNC THC module
- Dedicated THC co-processor with a position-aware FluidNC real-time interface
- Standalone external THC only if Z-position reconciliation and fail-safe control handoff are proven
- Controller migration only as a documented contingency if FluidNC cannot meet the locked requirement

The evaluation and acceptance tests are defined in `THC_ARCHITECTURE.md`.

### O-007 - Operator-software implementation

- Windows desktop application using a web-technology shell such as Tauri
- Native .NET desktop application
- Browser application hosted on a dedicated machine PC

The implementation must preserve an offline-capable local operator station and a documented FluidNC communications layer.

## Change rule

A locked decision can be changed when new measurements, component availability, cost, safety, or testing justify it. Record the replacement decision and preserve the old entry rather than silently rewriting project history.
