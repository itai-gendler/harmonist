---
appliesTo:
- type: capability
  id: undo-tag-changes
- type: entity
  id: tagging
  facts:
  - Files
references:
- kind: code
  role: implementation
  target: src/harmonist/tagger.py#revert_tags
---

# Undo reads every file before writing any

A missing or unreadable file, or a renamed file that cannot be told apart from another within the album, refuses the whole undo rather than leaving the album half reverted.
