---
appliesTo:
- type: entity
  id: artwork-backup
  effect: creates
- type: capability
  id: undo-artwork-change
references:
- kind: code
  role: implementation
  target: src/harmonist/artwork_store.py
- kind: doc
  role: intent
  target: docs/configuration.md
  title: '[artwork_store]'
---

# Artwork backups are removed only when the store is full, each album's last five changes last

Backups go only above the store's size limit (1 GB by default): first those outside each album's last five artwork changes, then the oldest. An addition needs no backup and stays undoable however full the store gets.
