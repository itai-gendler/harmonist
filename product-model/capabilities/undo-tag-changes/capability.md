---
availability:
- place: web
references:
- kind: code
  role: implementation
  target: src/harmonist/web/main.py#restore_tags
- kind: code
  role: implementation
  target: src/harmonist/tagger.py#revert_tags
- kind: code
  role: implementation
  target: src/harmonist/tag_history.py#revert_plan
- kind: doc
  role: intent
  target: docs/design/history.md
  title: Undoing a tagging
- kind: doc
  role: intent
  target: docs/troubleshooting.md
  title: Undoing things
---

# Undo tag changes

From a tagging in the album's History, the owner puts back the tag values those files carried before. The tagging is the unit, a field changed since is left alone, and every file is read before any is written.
