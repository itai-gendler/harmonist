---
appliesTo:
- type: entity
  id: tag-update
  effect: creates
permits:
- unattended: true
  when:
  - entity: settings
    fact: Library updates
    is: Find updates for review
- actors:
  - owner
references:
- kind: code
  role: implementation
  target: src/harmonist/config.py#GardenerConfig
- kind: doc
  role: intent
  target: docs/configuration.md
  title: '[gardener]'
---

# The background check finds tag updates only while Library updates is Find updates for review

Library updates is Off by default. The owner's own page views and settings changes find updates whatever it says; the timed check asks MusicBrainz only while it is Find updates for review, and reads the setting on every tick.

## Rationale

It writes nothing, so the default protects MusicBrainz, a volunteer-run service, from load nobody chose to start.
