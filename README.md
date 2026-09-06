# Æsc

**Terminal daemon.** Native Android APK. Repo: `novus-aesc`.

One of three components that run **independently**: Horizons-Ui (the UI), Æsc
(terminal), Æyre (voice/vision). Horizons-Ui is the *most* independent of the
three — it has its own browser, file pickers, chat interface and model loading,
and does not require either daemon. Any doc claiming the UI "cannot function
without" the daemons is superseded.

## Status

**Scaffold.** Nothing here runs yet. This repo exists to receive the Horizons
salvage and the Termux-era fold-in — build order targets #2 and #3.

## What this replaces

The Termux + Debian-proot setup currently carrying the terminal work. That
arrangement is **not permanent architecture** — it gets extracted into this APK
and then wiped from `aesop-xi`. Do not build anything assuming the proot stays.

## Salvage, don't preserve

Horizons-Ui is the donor repo. **Five targets only** — everything else goes to
the junkyard. Resist the urge to keep things because they work; keep them
because they're needed here.

| # | Target | Why it survives |
|---|---|---|
| 1 | **NPU loader** | The hard-won part. Model loading onto Hexagon. |
| 2 | **ADB loopback** ("the laptop trick") | `127.0.0.1:5555`, UID 2000. The sandbox-escape mechanism. |
| 3 | **Chromium integration** | Embedded browser surface. |
| 4 | **Terminal render** | The actual terminal drawing. |
| 5 | **Model router** | Routes requests to the right local model. |

Everything else in Horizons: **junkyard**.

## Known blocker — the Watchdog daemon

The existing Watchdog does not survive Android's process management. On MIUI,
One UI, and stock Android 13+, the system kills background processes and drops
long-running sessions with no warning.

**Fix: `ForegroundService`.** Not a `Service`, not a `WorkManager` job — a
foreground service with an ongoing notification, which is the only thing Android
reliably declines to kill. Until this is done, any long-running terminal session
is a coin flip.

(Operator-side mitigation that helps but is not a fix: Settings -> Developer
Options -> disable child-process restrictions for the app.)

## Planned layout

```
app/                  the APK source
  daemon/             terminal daemon core
  npu/                salvaged NPU loader
  adb/                salvaged ADB loopback
  render/             salvaged terminal render
  router/             salvaged model router
  watchdog/           ForegroundService rewrite
protocol/             IPC contracts (see below)
salvage/              staging area for Horizons extractions, with provenance
docs/
```

## IPC

Æsc talks to Æyre and Horizons-Ui over:

- **AF_UNIX sockets with `SCM_RIGHTS`** — FD-passing between daemons
- **WebSocket** — for the UI surface
- **ASharedMemory** — zero-copy buffers where it matters

Protocol specs live in `aesop-xi`, not here. This repo implements them.

## Beginner-Proof Standard

Every module states the problem it solves, its data flow, and its failure mode.
If a beginner dev or a third-rate model can't pick it up and resume, it gets
rewritten — not annotated.
