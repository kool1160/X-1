# X-1 Commissioning Checklist

Record dates, measurements, configuration commit, and results beside each item.

## Mechanical inspection

- [ ] Frame sits without rocking.
- [ ] Frame diagonals recorded.
- [ ] Master Y rail is straight and securely mounted.
- [ ] Second Y rail aligns through full travel without forcing the gantry.
- [ ] Y trucks have no perceptible rocking.
- [ ] Gantry is square after independent Y homing.
- [ ] X guide(s) are parallel and carriage motion is smooth.
- [ ] Z has no perceptible side play.
- [ ] Torch is trammed front-to-back and side-to-side.
- [ ] Hard stops prevent any carriage from leaving a guide.
- [ ] Rails, drive components, and cables are guarded from slag and pinch points.

## Electrical inspection

- [ ] Controller supply voltage and polarity verified.
- [ ] Motor supply voltage verified.
- [ ] Driver current settings recorded.
- [ ] Grounding and bonding points inspected.
- [ ] Cable shields and drain-wire termination documented.
- [ ] E-stop removes motion and torch-enable capability through hardware.
- [ ] Controller reports E-stop state correctly.
- [ ] Torch relay verified as isolated dry contacts.
- [ ] Plasma cutter remains disconnected during initial I/O tests.
- [ ] Arc OK isolation and electrical type verified before connection.
- [ ] Divided arc voltage is not connected to Jackpot GPIO.

## FluidNC motion tests

- [ ] Configuration file committed before testing.
- [ ] X direction correct.
- [ ] Y-left direction correct.
- [ ] Y-right direction correct.
- [ ] Z direction correct.
- [ ] All home switches report correctly.
- [ ] Float/probe switch reports correctly.
- [ ] Y homes and squares repeatedly.
- [ ] Soft limits prevent commanded overtravel.
- [ ] Commanded versus measured X travel recorded.
- [ ] Commanded versus measured Y travel recorded.
- [ ] Commanded versus measured Z travel recorded.
- [ ] Maximum stable speed and acceleration recorded with safety margin.
- [ ] Full-envelope dry G-code completes without binding or cable interference.

## Plasma tests

- [ ] Torch start tested with machine stationary.
- [ ] Torch stops immediately when commanded.
- [ ] Probe establishes material surface repeatably.
- [ ] Pierce height verified.
- [ ] Fixed cut height verified.
- [ ] Straight-line cut completed with THC disabled.
- [ ] Square cut completed and measured.
- [ ] Circle cut completed and measured.
- [ ] Lead-in/lead-out effects evaluated separately from machine motion.
- [ ] Cut parameters and consumable condition logged.
- [ ] Repeated cuts show stable motion and torch behavior.

## THC release gate

Do not begin THC commissioning until every required mechanical, electrical, FluidNC, and fixed-height plasma item above has passed.
