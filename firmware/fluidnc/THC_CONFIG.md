# X-1 THC Configuration Contract

**Status:** Interface template only. Names, ranges, units, and defaults are not released until the THC architecture is selected and bench-tested.

## Identity and compatibility

- THC architecture/revision:
- Hardware interface revision:
- Firmware build/commit:
- Compatible FluidNC base:
- Compatible X-1 Control version:
- Configuration schema version:

## Measurement

| Field | Units | Allowed range | Default | Source/verification |
|---|---|---|---|---|
| Divider ratio | ratio | TBD | TBD | Everlast measurement |
| Voltage scale | TBD | TBD | TBD | Simulator calibration |
| Voltage offset | V | TBD | TBD | Simulator calibration |
| Filter setting | TBD | TBD | TBD | Noise test |
| Minimum plausible voltage | V | TBD | TBD | Live baseline |
| Maximum plausible voltage | V | TBD | TBD | Interface rating/test |
| Signal-loss threshold | TBD | TBD | TBD | Failure test |

## Control

| Field | Units | Allowed range | Default | Notes |
|---|---|---|---|---|
| Target voltage | V | TBD | Material profile | Operator setting |
| Deadband | V | TBD | TBD | Prevent hunting |
| Stabilization delay | ms | TBD | TBD | After Arc OK |
| Maximum Z correction rate | mm/min | TBD | TBD | Mechanical/driver limit |
| Maximum correction distance | mm | TBD | TBD | Per cut/continuous TBD |
| Control gain(s) | TBD | TBD | TBD | Bench/live tuning |
| Velocity anti-dive threshold | % | TBD | TBD | Based on programmed/actual feed |
| Void/kerf-crossing response | enum | TBD | TBD | Architecture-dependent |

## State model

Required states:

- Disabled
- Armed
- Waiting for Arc OK
- Stabilizing
- Active
- Inhibited — velocity/corner
- Inhibited — invalid voltage
- Inhibited — cut loss
- Hold
- Fault

For every state, define:

- entry condition;
- allowed Z ownership;
- correction behavior;
- torch behavior;
- reported status;
- exit condition;
- recovery action.

## Commands from X-1 Control

Define exact command names and acknowledgement behavior for:

- read THC identity/capabilities;
- enable;
- disable;
- set target voltage;
- load validated material-profile settings;
- clear recoverable fault;
- request current configuration;
- save/restore configuration when permitted.

## Status reported to X-1 Control

Required fields:

- measured arc voltage;
- target voltage;
- Arc OK;
- enabled;
- active;
- state/inhibit reason;
- correction direction and rate;
- cumulative Z correction or synchronized Z position;
- measurement/interface health;
- fault code and message;
- configuration and firmware version.

## Failure behavior

Define and test:

- Arc OK loss;
- voltage input open/short/overrange;
- invalid divider configuration;
- Z limit activation;
- probe/float conflict;
- feed hold and resume;
- reset;
- E-stop;
- co-processor communication loss if applicable;
- USB/network loss to X-1 Control;
- controller restart or power interruption.

No configuration is released until the fields and failure behavior are supported by committed firmware and test records.
