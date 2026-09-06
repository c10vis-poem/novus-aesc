# Salvage staging

Extractions from `horizons-ui` land here **with provenance** before being
promoted into `app/`.

## Rules

1. **Record where it came from.** Every file gets a header comment or a sibling
   `.provenance` note: source repo, path, commit SHA, date pulled.
2. **Nothing gets promoted un-read.** If nobody has read it, it is not salvage,
   it is cargo.
3. **Junkyard is the default.** The five targets survive. Everything else does
   not, no matter how much work went into it.
4. **Don't fix while extracting.** Pull it, note what's wrong, promote, *then*
   fix. Mixing the two loses track of what changed.

## The five

- [ ] NPU loader
- [ ] ADB loopback
- [ ] Chromium integration
- [ ] Terminal render
- [ ] Model router

## The junkyard

Everything else. If it turns out something was needed, it is still in
`horizons-ui` git history — this is reversible, so bias toward cutting.
