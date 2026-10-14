---
appliesTo:
- type: capability
  id: confirm-suggestion
- type: capability
  id: assign-release
- type: capability
  id: apply-tag-updates
- type: capability
  id: apply-artwork
- type: capability
  id: undo-tag-changes
- type: capability
  id: undo-artwork-change
- type: capability
  id: sync-bandcamp
- type: capability
  id: redownload-album
- type: capability
  id: clear-musicbrainz-match
- type: capability
  id: forget-album
- type: capability
  id: change-album-origin
- type: capability
  id: erase-sidecars
- type: entity
  id: activity-entry
references:
- kind: code
  role: implementation
  target: src/harmonist/activity_store.py
- kind: doc
  role: intent
  target: docs/design/history.md
  title: Two records, one store
---

# Every change Harmonist makes is recorded in the Activity feed

Each outcome — a match, a tagging, an artwork change, an undo, a sync, a re-download, a cleared match, a forgotten album — is one Activity entry naming the album as it was, with every file, record and download change beneath it, and the entries are never pruned. Warnings Harmonist logs reach the feed by themselves.
