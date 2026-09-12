# unresolved.md — novus-aesc (Æsc)

1. **Document 05 vs. actual repo layout.** `05_FEDERATED_FILE_TREE_TOPOLOGY_MASTER.md`'s
   generic sketch of this repo (`npu_watchdog/`, `scripts/`, `process-isolation/`,
   `lmk-mitigation/`, `wireless-adb/`, `src/main/java/com/horizons/ui/adb/`) doesn't match
   the existing, more specific operator-declared plan (`laptop-trick-tunnel/`,
   `npu-watchdog/`, `protocol/`, `salvage/` with 5 named extraction targets). Not reconciled.
   Needs the user's call on which is authoritative.

2. **Unreviewed prior art in `aesop-xi`.** Bridge daemon (`deploy/phone/bridge/aesopd.py`),
   `llamad` daemon with NPU/Hexagon offload (`deploy/phone/daemons/`),
   `protocol/bridge-protocol.md`, `termux-helper` skill — merged from a remote branch,
   never reviewed, may already cover most of this repo's build target. See
   `novae-xorpus/unresolved.md` item 10.

3. **WebSocket auth** — not decided whether the Horizons-Ui-facing WebSocket surface
   authenticates, or how. Tracked here per `protocol/README.md`.

4. **Backpressure policy** — not decided for when the UI is slower than the daemon.
   Tracked here per `protocol/README.md`.

5. **Second master Drive folder not accessible.** `___Lex-Novi-Æxentis-Copiæ` (source for
   this repo's Document-05-mapped content, per the 14-subfolder table) hasn't been shared
   with this session. Nothing pulled from it.

6. **Watchdog ForegroundService rewrite** — not started. Current Watchdog doesn't survive
   Android process management on MIUI/One UI/Android 13+.
