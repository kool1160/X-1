# Architecture Notes

The X-1 software will be a dedicated machine application, not merely a G-code sender.

Initial proof-of-concept priorities:

1. Connect to FluidNC over USB serial.
2. Parse status reports into a stable machine-state model.
3. Home, jog, hold, resume, reset, and display coordinates.
4. Log controller traffic and faults.
5. Add network/WebSocket transport behind the same adapter.
6. Upload and run approved jobs from controller storage.

No torch command will be enabled in early software tests. Motion and communication will be proven with the plasma source disconnected.
