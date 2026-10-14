---
appliesTo:
- type: entity
  id: tag-update
  effect: changes
  to: Ignored
permits:
- actors:
  - owner
  when:
  - fact: Significance
    is-not: Settings
references:
- kind: code
  role: implementation
  target: src/harmonist/web/main.py#ignore_update
- kind: doc
  role: intent
  target: docs/design/tagging.md
  title: Transforms
---

# Only an update from MusicBrainz can be ignored

Ignoring waits for MusicBrainz to change, so an update that only brings an album into line with a tagging setting cannot be ignored; its remedy is the setting.
