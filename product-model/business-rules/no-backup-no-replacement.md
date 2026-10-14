---
appliesTo:
- type: entity
  id: artwork-backup
- type: capability
  id: apply-artwork
- type: capability
  id: apply-tag-updates
- type: capability
  id: confirm-suggestion
references:
- kind: code
  role: implementation
  target: src/harmonist/artwork_store.py#keep_all
- kind: doc
  role: intent
  target: docs/design/artwork.md
  title: A backup is what permits a replacement
---

# An image is replaced only once a copy of it is kept

Every image a change is about to replace is kept in the artwork store first, all together; a target whose image cannot be kept is left as it is, while tags and additions still go ahead. With the store's size set to zero, no artwork is replaced at all.

## Rationale

A replacement that could not be undone would destroy the only copy of the owner's image.
