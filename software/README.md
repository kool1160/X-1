# X-1 Operator Software

This directory contains the dedicated software used to operate the X-1 plasma table.

FluidNC or a controlled X-1 FluidNC fork remains the embedded motion-control firmware on the Jackpot controller. X-1 Control is a separate Windows application that connects to FluidNC and presents a complete plasma-machine interface rather than a generic G-code sender.

Required capabilities include:

- machine connection and health status;
- homing and automatic gantry squaring;
- axis jogging, continuous jog, step jog, and zeroing;
- material and cut-profile management;
- G-code import, validation, preview, and job queue;
- sheet origin and work-offset setup;
- perimeter trace and torch-inhibited dry-run modes;
- probe, pierce-height, cut-height, and torch-control workflows;
- Arc OK, float switch, limits, E-stop, and alarm display;
- run, pause, resume, stop, and cut-recovery controls;
- live position, feed, job progress, elapsed time, and estimated remaining time;
- automatic THC enable/disable, target voltage, live voltage, active/inhibited state, and fault display;
- THC voltage/correction logs and configuration compatibility checks;
- event logging, fault history, configuration backup, and diagnostics.

## Development limit during Phase 1

Active software work is limited to:

- selecting the application stack through a communication proof;
- implementing USB transport first and network transport second;
- parsing FluidNC startup, status, alarm, and acknowledgement messages;
- establishing the machine-state model and traffic logging;
- documenting the future THC command/status contract.

Do not drift into full CAD, CAM, nesting, quoting, cloud, mobile, AI, or commercial features during the current phase.

## Safety boundary

X-1 Control must not bypass hardware safety. E-stop, torch inhibit, plasma isolation, and controller-side fault responses remain independent of the Windows application. Real-time THC correction cannot depend on round-trip communication through the application.

See `docs/OPERATOR_SOFTWARE.md` and `docs/THC_ARCHITECTURE.md` for the controlled architecture.
