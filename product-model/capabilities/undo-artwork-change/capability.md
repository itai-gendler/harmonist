---
availability:
- place: web
references:
- kind: code
  role: implementation
  target: src/harmonist/web/main.py#restore_artwork
- kind: code
  role: implementation
  target: src/harmonist/tagger.py#restore_artwork
- kind: doc
  role: intent
  target: docs/design/history.md
  title: Undoing an artwork change
---

# Undo an artwork change

From an artwork change in the album's History, the owner puts back the images it replaced and takes off the ones it added. Undoing artwork never touches tags.
