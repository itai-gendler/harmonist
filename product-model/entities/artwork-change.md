---
relations:
- entity: artwork-backup
  verb: keeps
  cardinality: many-to-many
references:
- kind: code
  role: implementation
  target: src/harmonist/tag_history.py#artwork_revert_plan
- kind: doc
  role: intent
  target: docs/design/history.md
  title: Undoing an artwork change
---

# Artwork change

One write of artwork to an album, recorded with the image each target held before and after, so it can be undone separately from tags.

## Information kept

- **Kind** — an addition fills an empty place; a replacement overwrites an image
- **Targets** — each track or folder cover written, with the image before and after
- **Written at** — when the artwork was written
