# Æsc — terminal daemon

Canon name: **Æsc**. Repo name: `novus-aesc`. See `novae-xorpus/NAMING-CANON.md`.

## What this is

The terminal daemon layer of the Æsop-Xi stack. Provides OS-level shell
access, accessibility services, and Termux-free command execution on Android.
Part of the 3-APK architecture alongside Horizons-Ui and Æyre.

## Stack position

```
Æsop-Xi → NovÆxenti → NovÆxopia → Æsc (this repo)
                                 → Æyre (voice/vision)
```

Æsc runs independently. Horizons-Ui does NOT require Æsc to function — any
document claiming otherwise is superseded by the naming canon.

## Conventions

- `laptop-trick-tunnel/` — ADB-to-WebSocket local Unix host bridge logic.
- `npu-watchdog/` — real-time Genie SDK thermal and OOM monitoring loop.
- Protocol specs in `protocol/` — daemon lifecycle, IPC contract, permissions.
- Reference docs in `docs/` — Android accessibility API notes, shell execution
  patterns.
- Salvaged material in `salvage/` — content from earlier "Æsh" / "daemon.aexenti"
  designs, preserved for reference.

## Operator Rule 0 — no action without explicit order

A skipped or unanswered question is NOT consent. State the concrete plan and
get an explicit go-ahead before any state-changing action, even a local and
easily reversible one.

## Operator Rule 1 — read this file and RESUME.md first

Before doing anything else in this repo, read this CLAUDE.md and RESUME.md.
Standing convention across the operator's repos for months — step one,
every session, no exceptions.

## Git workflow

PR required. No direct pushes to main. CI runs gitleaks + structure check.
Before every push, scan the diff for secrets/keys and refuse to push if any
are found. On green CI, auto-merge into `main` immediately — do not wait for
a manual merge step. Leave the branch in place after merge; do not delete it.
