# PENDING.md — novus-aesc (Æsc)

Durable cross-session backlog. Not rewritten each session — items persist until resolved or explicitly dropped.

- **Blocked on DroidDesk install** (build order #1 in `docs/BUILD-ORDER.md`) — this repo is build order #2, do not re-sequence.
- **Watchdog daemon doesn't survive Android process management** (MIUI/One UI/Android 13+ kill it). Fix is a `ForegroundService`, not yet built.
- **5 salvage targets not yet pulled from `horizons-ui`** — NPU loader, ADB loopback, Chromium integration, terminal render, model router. All unchecked in `salvage/README.md`.
- **Prior art in `aesop-xi` never reviewed** — a bridge daemon (`deploy/phone/bridge/aesopd.py`), a supervised `llamad` daemon, `protocol/bridge-protocol.md`, and a `termux-helper` skill already exist there and may cover most of this repo's task.
