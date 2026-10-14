---
appliesTo:
- type: entity
  id: album
  effect: changes
permits:
- actors:
  - owner
- unattended: true
references:
- kind: doc
  role: intent
  target: docs/security.md
  title: Security
---

# Only the owner, or Harmonist on its own, changes an album

Harmonist serves one person: the owner's actions and Harmonist's own scans, syncs and checks are the only changes made to an album.
