# Where Æsc sits in the build order

Operator-declared. **Do not re-sequence.**

1. **DroidDesk install** — phone + tablet. Termux:X11 rendering, standalone
   desktops per device (not phone->tablet mirroring; scrcpy explicitly ruled out).
2. **Æsc terminal daemon setup** <- *this repo* — salvage the five targets,
   fix Watchdog via ForegroundService.
3. **Fold Termux-era work into Æsc** — rewrite the scripts for the native APK.

Not started until the above are done: grill session, Œræcle wiring, model
weights into `novaexopia`, DeepSeek harness spec, vendor-workspace skill.

## Prior art to read before starting

`novae-xorpus/unresolved.md` item 10 — a bridge daemon (`deploy/phone/bridge/aesopd.py`),
a supervised `llamad` daemon with real NPU/Hexagon offload (`deploy/phone/daemons/`),
`protocol/bridge-protocol.md`, and a `termux-helper` skill already exist in
`aesop-xi`, merged from a remote branch and never reviewed. **That may already be
most of this task.** Read it before writing anything new.
