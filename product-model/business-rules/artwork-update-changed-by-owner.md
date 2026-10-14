---
appliesTo:
- type: entity
  id: artwork-update
  effect: changes
permits:
- actors:
  - owner
references:
- kind: doc
  role: intent
  target: docs/security.md
  title: Security
---

# Only the owner changes an artwork update

Applying artwork is the owner's decision; Harmonist's background check only proposes.
