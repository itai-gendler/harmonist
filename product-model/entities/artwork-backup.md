---
references:
- kind: code
  role: implementation
  target: src/harmonist/artwork_store.py
- kind: doc
  role: intent
  target: docs/configuration.md
  title: '[artwork_store]'
---

# Artwork backup

A kept copy of an image Harmonist replaced, held in the configuration folder within a size limit so the replacement can be undone.

## Information kept

- **Image** — the replaced image, named by its digest
- **Recent** — it backs one of its album's last five artwork changes, which are removed last when the store is full
