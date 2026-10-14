---
availability:
- place: web
references:
- kind: code
  role: implementation
  target: src/harmonist/web/main.py#undo_rematch
- kind: doc
  role: intent
  target: docs/design/history.md
  title: Undoing a tagging
---

# Restore a cleared MusicBrainz match

The Undo beside a cleared match links the album back to the release its files still carry, needing nothing stored, since clearing the match left the tags alone.
