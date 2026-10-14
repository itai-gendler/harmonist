---
availability:
- place: web
references:
- kind: code
  role: implementation
  target: src/harmonist/artwork_updates.py#sweep
- kind: doc
  role: intent
  target: docs/design/artwork.md
  title: Finding changes without opening an album
---

# Find artwork updates in the background

Under the same Library updates setting, Harmonist asks the Cover Art Archive about albums in small, oldest-first batches within the archive's freshness interval, independently of tag updates, and proposes additions and replacements without writing to the music files.
