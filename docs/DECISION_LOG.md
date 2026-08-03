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

### D-008 - Half-sheet support area versus cut travel

- **Decision:** X-1 shall provide approximately 50 × 50 inches of clear sheet-support area so an untrimmed 48 × 48 inch half-sheet can be loaded with about 1 inch of clearance on each side.
- **Clarification:** The cutting envelope is a separate dimension and is not required to equal 48 × 48 inches. Gantry trucks, carriage width, torch offset, limits, supports, and overtravel may reduce usable cut travel.
- **Reason:** Half-sheet compatibility is the important capability missing from many small plasma tables. The existing large laser already handles long work.
- **Cost rule:** Prefer the shortest standard motion components that satisfy the support-area requirement and deliver a useful cut envelope. Do not buy longer screws or rails merely to maximize travel.
- **Status:** Locked requirement; exact cut travel open until hardware selection
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

### D-012 - Main-axis ball-screw direction

- **Decision:** Use ball-screw drives for X, Y-left, and Y-right.
- **Diameter baseline:** 16 mm nominal, approximately 5/8 inch, is the minimum main-axis candidate.
- **Reason:** Main-axis loads are light, but a roughly four-foot screw span is limited by critical rotational speed and whip. A 12 mm, approximately 1/2-inch, screw gives away too much speed margin for the baseline design.
- **Open details:** Exact lead, length, root diameter, end machining, bearing support arrangement, nut style, coupler, motor, and delivered cost.
- **Z axis:** May use a smaller screw or compact purchased slide.
- **Status:** Architecture and minimum candidate locked; exact package open
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

### O-003 - Main-axis ball-screw package

- Exact 16 mm screw series and lead
- Exact overall lengths and usable strokes
- Fixed-supported versus fixed-fixed bearing arrangement
- Ball nut, housing, couplers, and motor interfaces
- Critical-speed and rapid-speed verification

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
