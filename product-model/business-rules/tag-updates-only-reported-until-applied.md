---
appliesTo:
- type: entity
  id: tag-update
- type: capability
  id: check-for-tag-updates
- type: capability
  id: apply-tag-updates
references:
- kind: code
  role: implementation
  target: src/harmonist/gardener.py#sweep
- kind: doc
  role: intent
  target: docs/design/tagging.md
  title: How significant a change is
---

# A tag update is written only when the owner applies it

Finding an update — on opening an album, after a settings change or in the background check — only lists it; every significance level needs the owner's review, so the background check can never change the library.
