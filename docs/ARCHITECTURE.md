# X-1 System Architecture

## Mechanical stack

```text
Removable exterior skins and guards
                |
Welded tube structural frame
                |
Adjustable rail pads / mounting faces
                |
Purchased X/Y linear guides and metal trucks
                |
Independent Y-left and Y-right drive systems
                |
Lightweight tube gantry with X guide and drive
                |
Metal Z slide, torch mount, and probing mechanism

Separate internal structure:
water pan -> slat holders -> slats -> workpiece
```

The water pan and slats sit inside the structural frame but do not define rail alignment.

## Motion-channel assignment

The Jackpot has enough driver positions for the intended machine layout. The conceptual assignment is:

| Channel | Function | Notes |
|---|---|---|
| X | X carriage | Gantry-axis motion |
| Y | Y-left | Independent homing switch |
| A | Y-right | Independent homing switch; slaved during normal motion |
| Z | Torch height | Probe, pierce height, fixed cut height |
| B | Reserved | Rotary or future accessory |
| C | Reserved | Future accessory or test channel |

Final socket assignment and GPIO mapping must be verified against the exact Jackpot documentation and the installed FluidNC build before wiring.

## Control signal flow

```text
Laptop / phone / shop network
             |
        Wi-Fi / USB
             |
Jackpot controller running FluidNC
     |          |          |
 motion      switches    outputs
     |          |          |
 X/Y1/Y2/Z   homes,     isolated torch
 motors       float,     start relay
              E-stop

Everlast PowerPlasma 82i
     |                  |
 torch-start input    Arc OK / divided voltage
     |                  |
 dry contact only     isolation required
```

## Initial operating mode

Revision 1 of the machine should operate without active arc-voltage THC:

1. Home and square Y.
2. Move to pierce location.
3. Probe material with the floating head or approved probe method.
4. Retract to pierce height.
5. Close isolated torch-start contact.
6. Wait for configured pierce delay and Arc OK if implemented.
7. Move to fixed cut height.
8. Execute the toolpath.
9. Open torch-start contact at the end of the cut.

This staged approach keeps controller, CAM, probing, and mechanical problems separate from THC development.

## Electrical zones

The enclosure should be divided into functional zones:

- **AC/mains:** disconnect, contactor/safety relay, protected power supplies.
- **Motor power:** 24-48 VDC supply and external drivers if used.
- **Controller:** Jackpot, USB/network service access, low-voltage distribution.
- **Plasma interface:** isolated torch relay, Arc OK isolation, future voltage interface.
- **Field terminals:** motors, switches, cable-chain wiring, grounding/bonding.

Torch lead, work lead, motor power, and low-level switch/voltage wiring should be routed separately wherever practical.

## Data and configuration

The repository will eventually contain:

- released SolidWorks models and drawings;
- DXF cut files;
- FluidNC machine configuration;
- pin/I/O map;
- driver-current and microstep settings;
- calibration results;
- cut-test logs;
- photos and as-built changes.
