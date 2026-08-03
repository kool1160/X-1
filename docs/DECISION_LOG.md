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

### D-007 - Initial cutting mode

- **Decision:** Commission motion, probing, torch control, and fixed-height cutting before developing or integrating THC.
- **Status:** Locked
- **Date:** 2026-08-02

### D-008 - Machine length

- **Decision:** Do not force a nominal 4 x 8 or 4 x 6 size before component selection. Final Y travel will be based on the best-value standard guide and drive lengths.
- **Target:** Approximately 60-72 inches of usable Y travel.
- **Status:** Locked approach; final dimension open
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

### O-006 - THC path

- Standalone THC
- Custom FluidNC development
- Later migration to another controller

## Change rule

A locked decision can be changed when new measurements, component availability, cost, safety, or testing justify it. Record the replacement decision and preserve the old entry rather than silently rewriting project history.
