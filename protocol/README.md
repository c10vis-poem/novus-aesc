# IPC — what Æsc speaks

Specs are authored in `aesop-xi`. This file records what this daemon
**implements** and where the contracts live.

| Channel | Transport | Used for |
|---|---|---|
| Daemon <-> daemon | `AF_UNIX` + `SCM_RIGHTS` | FD passing between Æsc and Æyre |
| Daemon <-> UI | WebSocket | Horizons-Ui terminal surface |
| Bulk buffers | `ASharedMemory` | Zero-copy where copying would hurt |
| Host escape | ADB loopback `127.0.0.1:5555`, UID 2000 | "The laptop trick" |

## Process isolation

Each daemon runs in its own Android process (`AndroidManifest` `android:process`).
That is deliberate: one daemon crashing must not take the others down. It also
means every cross-daemon call is real IPC, not a method call — design for that,
don't fight it.

## Not decided yet

- Whether the WebSocket surface authenticates, and how
- Backpressure policy when the UI is slower than the daemon

Track these in `novae-xorpus/unresolved.md`, not here.
