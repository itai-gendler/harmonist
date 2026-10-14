---
appliesTo:
- type: capability
  id: accept-album-as-complete
- type: entity
  id: album
  facts:
  - Accepted as complete
references:
- kind: code
  role: implementation
  target: src/harmonist/web/main.py#set_tracks_unavailable
---

# Only an incomplete album can be accepted as complete

The acceptance records that the owner wants its shortfall to stop being flagged, so it is offered only on an album that is really short; it changes no state, tag or file.
