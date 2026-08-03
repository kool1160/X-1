# X-1 Operator Software

This directory will contain the dedicated software used to operate the X-1 plasma table.

FluidNC remains the embedded motion-control firmware on the Jackpot controller. The X-1 operator software is a separate application that connects to FluidNC and presents a complete plasma-machine interface rather than a generic G-code sender.

Planned capabilities include:

- machine connection and health status;
- homing and automatic gantry squaring;
- axis jogging, continuous jog, step jog, and zeroing;
- material and cut-profile management;
- G-code import, validation, preview, and job queue;
- sheet origin and work-offset setup;
- perimeter trace and dry-run modes;
- probe, pierce-height, cut-height, and torch-control workflows;
- Arc OK, float switch, limits, E-stop, and alarm display;
- run, pause, resume, stop, and cut-recovery controls;
- live position, feed, job progress, elapsed time, and estimated remaining time;
- event logging, fault history, configuration backup, and diagnostics;
- future THC controls and voltage visualization after the THC architecture is proven.

The software must not bypass hardware safety. E-stop, torch inhibit, and other critical safety functions remain hardwired.
