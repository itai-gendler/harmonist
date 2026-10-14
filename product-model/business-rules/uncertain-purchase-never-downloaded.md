---
appliesTo:
- type: entity
  id: bandcamp-purchase
  effect: changes
  to: Potential download
- type: capability
  id: sync-bandcamp
references:
- kind: code
  role: implementation
  target: src/harmonist/bandcamp_hook.py#HarmonistSyncer
- kind: doc
  role: intent
  target: docs/design/bandcamp.md
  title: Download destinations
---

# A purchase is never downloaded on a guess

A purchase the sync cannot confidently tie to an album, or whose download folder holds something that does not prove it is that purchase, is not downloaded and not marked as downloaded; it waits as a potential download for the owner to decide.
