# X-1 On-Hand Hardware Inventory

**Status:** To be completed under issue #5 before buying replacement controls or motion hardware.

| ID | Category | Manufacturer/model | Qty | Condition | Key ratings/dimensions | Reuse decision | Evidence/location |
|---|---|---|---:|---|---|---|---|
| SRC-001 | CNC plasma source | LOTOS LTP5500DCNC | 1 | On hand; previously ran on JD's Garage table | 20–55 A on 220/240 V; 20–35 A on 110/120 V; non-HF blowback pilot arc; CNC torch-start interface; 1:1 raw arc-voltage/THC output; machine torch on hand | Baseline production-source candidate; controlled 10–18 gauge testing required | Owner photo; official LOTOS product/manual; issue #15 |
| SRC-002 | CNC plasma source | Everlast PowerPlasma 82i | 1 | On hand | 20–80 A; machine torch; CNC interface/divided voltage previously investigated | Development/comparison source | Existing table and project records; issue #15 |
| CTRL-001 | Controller | V1 Engineering Jackpot CNC Controller V1.2.1 | 1 | On hand | TBD board/ESP32/firmware details | Evaluate; no longer assumed production controller | Photos required |
| DRV-001 | Stepper driver | TMC2209 modules installed on Jackpot | TBD | On hand | Current/microstep settings TBD | Evaluate | Photos/settings required |
| DRV-002 | External stepper drive | KL-5056 or available equivalent | TBD | On hand | Voltage/current/microstep range TBD | Evaluate | Model/terminal photos required |
| MOT-001 | NEMA 23 motor | TBD | TBD | On hand | Current, torque, shaft, cable TBD | Evaluate | Nameplate photos required |
| PSU-001 | Power supply | TBD | TBD | On hand | Output voltage/current TBD | Evaluate | Nameplate/meter test required |
| ENC-001 | Enclosure | TBD | TBD | On hand | Internal size TBD | Evaluate | Measurements required |
| SW-001 | Home/limit switch | TBD | TBD | On hand | Contact type/voltage TBD | Evaluate | Continuity test required |
| REL-001 | Relay/contactor | TBD | TBD | On hand | Coil/contact/isolation rating TBD | Evaluate | Datasheet required |

## LOTOS source record still required

- exact machine-torch manufacturer/model and lead length;
- installed nozzle/electrode/shield part numbers;
- available nozzle-orifice and amperage options;
- exact mating CNC/THC connectors and cables on hand;
- verify torch-start contact requirements and pinout on this exact unit;
- verify whether a separate Arc OK contact is present and document its electrical behavior;
- verify 1:1 raw arc-voltage polarity and loaded voltage during controlled cuts;
- design the required isolated high-voltage divider/THCAD interface before connecting arc voltage to any controller;
- document 220/240 V branch circuit and actual air system;
- record prior JD's Garage cut results and known problems.

## Required controller record

- Jackpot board revision:
- ESP32 module model:
- Installed FluidNC version:
- Current configuration filename:
- Configuration backup commit/path:
- Installed driver modules by socket:
- Power-input voltage and polarity:
- Available screw-terminal inputs/outputs:
- Expansion hardware:
- Known damage or modifications:

## Required motor/driver record

For every motor and drive, record:

- exact model;
- nameplate data;
- shaft diameter and length;
- connector/cable condition;
- phase resistance/continuity where appropriate;
- drive input type and terminal labels;
- supply-voltage range;
- current setting;
- microstep setting;
- mounting pattern;
- test result at low speed/current;
- selected axis or rejection reason.

## Required power and safety record

- available 24 V, 36 V, and 48 V supplies;
- mains disconnect/contactors;
- E-stop components;
- fusing/breakers;
- terminal blocks and grounding hardware;
- shielded motor and signal cable;
- isolated relays or optocouplers;
- cabinet fans/filters;
- cable chain.

Do not mark an item reusable until ratings, condition, and compatibility are verified.
