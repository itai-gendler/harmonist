---
references:
- kind: code
  role: implementation
  target: src/harmonist/tag_history.py
- kind: code
  role: implementation
  target: src/harmonist/activity_store.py
- kind: doc
  role: intent
  target: docs/design/history.md
  title: History and undo
---

# Tagging

One write of a release's tags to an album, recorded field by field and file by file so the album's History can show what changed and Undo tag changes can put it back.

## Information kept

- **Release** — the release whose tags were written
- **Field changes** — each owned field's value before and after, per file
- **Files** — each file written, named by file name, release-track ID, recording ID and disc and track position
- **Written at** — when the tags were written
