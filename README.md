# X-1

**Laser X Design X-1 CNC Plasma Table**

X-1 is a clean-sheet CNC plasma-table project built around Chris Hilton's fabrication capability, available 1/8-inch-wall tube, laser-cut/formable sheet metal, a V1 Engineering Jackpot controller, and FluidNC.

The project is intentionally **not** a direct clone of either reference machine. The JD's Garage and CrossFire PRO MAX material is being used to study proportions, motion layouts, assembly order, alignment methods, water-pan construction, and low-cost component choices. X-1 will use a welded tube structure, purchased linear guides, metal carriages, removable cosmetic skins, and a drive system selected for cost, serviceability, and available standard lengths.

## Current status

**Phase:** Rev A concept and component selection  
**Nominal work envelope:** 48 inches wide; final length will be set by the selected standard rail and drive-component lengths, likely about 60-72 inches.  
**Controller:** V1 Engineering Jackpot CNC Controller V1.2.1  
**Firmware:** FluidNC  
**Plasma source:** Everlast PowerPlasma 82i

## Decisions already made

- The machine is named **X-1 - Laser X Design 1**.
- The primary structure will be welded from available 1/8-inch-wall tube.
- Sheet metal will be used where it adds value: carriages, brackets, guards, pan, enclosure, slat holders, and removable exterior skins.
- Structural motion parts will be metal. 3D-printed parts may be used only for noncritical jigs, covers, spacers, or prototypes.
- X and Y will use purchased linear guides; the exact guide family and size remain open.
- The gantry will use independent left/right Y drives and separate home switches for automatic squaring.
- The water/slat structure will not be the precision reference for the motion rails.
- The first operating milestone is reliable fixed-height cutting. THC is a later phase.

## Open engineering decisions

1. **Y guide:** SBR20 supported round rail or HGR20 profile rail.
2. **X guide:** SBR16/SBR20 or HGR15/HGR20.
3. **X/Y drive:** rack and pinion, timing belt, or ball screw.
4. **Machine length:** determined from the best-value standard guide and drive lengths.
5. **Motors/drivers:** Jackpot-mounted TMC2209 modules or external step/direction drives.
6. **Z assembly:** fabricated metal slide or purchased compact Z module.
7. **THC architecture:** standalone controller, custom FluidNC work, or later controller migration.

## Source material

- [X-1 Preliminary Engineering and Build Plan - Rev A](X-1_CNC_Plasma_Table_Preliminary_Build_Plan_Rev_A.pdf)
- [CrossFire PRO MAX Assembly Guide](CrossFire%20PRO%20MAX%20Assembly%20Guide%20_%20Langmuir%20Systems.pdf)
- [JD's Garage Imperial reference package](Imperial%20Version-20260802T230932Z-1-001.zip)

These files are references, not released X-1 manufacturing drawings. Verify the original license and redistribution terms before publishing or redistributing third-party material.

## Repository map

- [`docs/`](docs/) - requirements, architecture, decision work, development sequence, and project status
- [`references/`](references/) - reference-file index and usage notes
- [`cad/`](cad/) - future SolidWorks assemblies and source models
- [`drawings/`](drawings/) - released PDFs, DXFs, hole tables, and cut files
- [`bom/`](bom/) - component research and released bills of material
- [`firmware/fluidnc/`](firmware/fluidnc/) - FluidNC configuration and commissioning notes
- [`testing/`](testing/) - inspection, alignment, and commissioning records

## Immediate design gate

Before releasing Rev B drawings, select actual listings for:

- Y linear guides and blocks
- X linear guides and blocks
- X/Y drive components and standard lengths
- Motors, external drivers if used, couplers/pulleys, and end supports
- Z-axis guide and drive

After those parts are selected and measured, Rev B can contain final overall dimensions, tube cut lengths, rail-hole patterns, metal carriage DXFs, motor brackets, wiring schedules, and a working FluidNC machine configuration.

## Safety

This repository is an engineering-development workspace, not a certification. Plasma arc voltage, mains wiring, automatic motion, fumes, hot material, fire, pinch points, and UV/IR exposure can cause severe injury or death. The finished machine requires verified grounding, isolation, hardwired emergency-stop behavior, ventilation, fire controls, guarding, and confirmed plasma-interface pinouts before operation.
