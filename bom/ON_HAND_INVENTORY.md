# X-1 On-Hand Hardware Inventory

**Status:** To be completed under issue #5 before buying replacement controls or motion hardware.

| ID | Category | Manufacturer/model | Qty | Condition | Key ratings/dimensions | Reuse decision | Evidence/location |
|---|---|---|---:|---|---|---|---|
| CTRL-001 | Controller | V1 Engineering Jackpot CNC Controller V1.2.1 | 1 | On hand | TBD board/ESP32/firmware details | Baseline controller | Photos required |
| DRV-001 | Stepper driver | TMC2209 modules installed on Jackpot | TBD | On hand | Current/microstep settings TBD | Evaluate | Photos/settings required |
| DRV-002 | External stepper drive | KL-5056 or available equivalent | TBD | On hand | Voltage/current/microstep range TBD | Evaluate | Model/terminal photos required |
| MOT-001 | NEMA 23 motor | TBD | TBD | On hand | Current, torque, shaft, cable TBD | Evaluate | Nameplate photos required |
| PSU-001 | Power supply | TBD | TBD | On hand | Output voltage/current TBD | Evaluate | Nameplate/meter test required |
| ENC-001 | Enclosure | TBD | TBD | On hand | Internal size TBD | Evaluate | Measurements required |
| SW-001 | Home/limit switch | TBD | TBD | On hand | Contact type/voltage TBD | Evaluate | Continuity test required |
| REL-001 | Relay/contactor | TBD | TBD | On hand | Coil/contact/isolation rating TBD | Evaluate | Datasheet required |

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
