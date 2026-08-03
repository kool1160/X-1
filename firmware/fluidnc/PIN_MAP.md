# X-1 Jackpot / FluidNC Pin Map

**Status:** Unverified template. Do not wire from this file until every entry is confirmed against the actual Jackpot board, installed FluidNC build, and electrical measurements.

| Function | Jackpot socket/terminal | GPIO or internal channel | Active state | Voltage/interface | Cable/terminal destination | Verified | Evidence |
|---|---|---|---|---|---|---|---|
| X step/driver | TBD | TBD | — | TBD | X motor/driver | No | |
| Y-left step/driver | TBD | TBD | — | TBD | Y-left motor/driver | No | |
| Y-right step/driver | TBD | TBD | — | TBD | Y-right motor/driver | No | |
| Z step/driver | TBD | TBD | — | TBD | Z motor/driver | No | |
| X home/limit | TBD | TBD | TBD | Isolated/switch input TBD | X switch | No | |
| Y-left home | TBD | TBD | TBD | Isolated/switch input TBD | Y-left switch | No | |
| Y-right home | TBD | TBD | TBD | Isolated/switch input TBD | Y-right switch | No | |
| Z home/upper limit | TBD | TBD | TBD | Isolated/switch input TBD | Z switch | No | |
| Float/probe | TBD | TBD | TBD | Isolated/switch input TBD | Torch float switch | No | |
| E-stop status | TBD | TBD | TBD | Isolated status only | Safety circuit auxiliary contact | No | |
| Torch command | TBD | TBD | TBD | Output to isolated dry-contact relay | Everlast torch-start pins | No | |
| Arc OK | TBD | TBD | TBD | Verified isolated input | Everlast Arc OK | No | |
| Arc-voltage input | TBD | TBD | — | Isolated/protected interface only | Everlast DV+/DV- interface | No | |
| THC enable/status | TBD | TBD | TBD | Firmware/protocol | X-1 Control | No | |

## Verification checklist

- [ ] Board revision and ESP32 module photographed
- [ ] Board schematic or official documentation located
- [ ] Each motor socket mapped
- [ ] Each input terminal mapped
- [ ] Each output terminal mapped
- [ ] Active states tested with a meter/safe signal
- [ ] Pull-up/pull-down behavior verified
- [ ] Input voltage tolerance verified
- [ ] Output electrical type verified
- [ ] Plasma-related signals isolated
- [ ] FluidNC configuration matches the physical map
- [ ] X-1 Control status names match the firmware map

## Safety notes

- E-stop status is not the E-stop safety function; the hardwired circuit must remove motion and torch capability.
- Torch start must close a verified isolated dry contact only.
- Never connect raw or divided arc voltage directly to Jackpot or ESP32 GPIO.
- Record every wiring revision and update the as-built terminal schedule.
