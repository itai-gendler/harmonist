---
appliesTo:
- type: capability
  id: undo-tag-changes
- type: capability
  id: undo-artwork-change
references:
- kind: code
  role: implementation
  target: src/harmonist/tagger.py#revert_tags
- kind: code
  role: implementation
  target: src/harmonist/tagger.py#restore_artwork
- kind: doc
  role: intent
  target: docs/design/history.md
  title: Undoing a tagging
---

# Undo never touches what changed after the change it undoes

A tag field, track image or folder cover goes back only if it still carries what that change wrote; anything edited since, in another tool or by a later change, is kept and named in the result. Undoing tags never touches artwork, and undoing artwork never touches tags.
