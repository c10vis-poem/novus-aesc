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

- Protocol specs in `protocol/` — daemon lifecycle, IPC contract, permissions.
- Reference docs in `docs/` — Android accessibility API notes, shell execution
  patterns.
- Salvaged material in `salvage/` — content from earlier "Æsh" / "daemon.aexenti"
  designs, preserved for reference.

## Git workflow

PR required. No direct pushes to main. CI runs gitleaks + structure check.
