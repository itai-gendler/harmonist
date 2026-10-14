---
appliesTo:
- type: capability
  id: confirm-suggestion
- type: capability
  id: switch-release
- type: capability
  id: edit-track-assignments
- type: capability
  id: apply-artwork
references:
- kind: code
  role: implementation
  target: src/harmonist/web/main.py#album_artwork_update
- kind: doc
  role: intent
  target: docs/design/artwork.md
  title: Writing only what was shown
---

# A reviewed change is written only if it still matches what was shown

Confirming, switching, accepting assignments and applying artwork rebuild the change from disk and MusicBrainz's kept copy and write only when it matches the review the owner saw; otherwise nothing is written and the review is shown again. Each target is re-read just before it is written, and one changed in between is left alone.
