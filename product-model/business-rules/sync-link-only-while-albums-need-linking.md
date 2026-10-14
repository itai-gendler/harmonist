---
appliesTo:
- type: capability
  id: sync-bandcamp
- type: entity
  id: album
  effect: changes
  from: Needs Linking
  to: Complete
references:
- kind: code
  role: implementation
  target: src/harmonist/web/main.py#create_app
- kind: doc
  role: intent
  target: docs/design/bandcamp.md
  title: A first sync must never re-download a library
---

# A sync downloads nothing while any album waits under Needs Linking

While an album waits to be linked to its purchase, a sync pages the whole collection and only links purchases to albums on disk; downloads resume once nothing is left to link. The owner can override the mode for a single sync with the Link-only box.

## Rationale

An owner adopting an existing library already has most purchases on disk under names the sync does not know; a first sync must never download them again.
