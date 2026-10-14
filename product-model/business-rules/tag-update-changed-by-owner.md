---
appliesTo:
- type: entity
  id: tag-update
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

# Only the owner, or Harmonist on its own, changes a tag update

The owner applies, ignores and stops ignoring updates; Harmonist's own check lists an ignored update again when MusicBrainz changes.
