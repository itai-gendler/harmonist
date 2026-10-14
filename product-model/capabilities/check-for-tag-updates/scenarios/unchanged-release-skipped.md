---
kind: alternative
routes:
  web: Web
steps:
- text: Ten minutes pass while Library updates is Find updates for review
  kind: condition
  unattended: true
  entities:
  - entity: settings
    effect: reads
    facts:
    - Library updates
  contexts:
    web:
      place: web::library
- text: The Product reads an album's release fresh from MusicBrainz
  kind: product
  entities:
  - entity: release
    effect: changes
    facts:
    - Last read
  - entity: album
    effect: reads
    facts: []
  contexts:
    web:
      place: web::library
- text: The release is identical to the copy kept
  kind: condition
  entities: []
  contexts:
    web:
      place: web::library
- text: The Product moves on without reading the album's files, leaving its update as it was
  kind: product
  entities:
  - entity: tag-update
    effect: reads
    facts:
    - Significance
  - entity: album
    effect: reads
    facts: []
  contexts:
    web:
      place: web::library
---

# Skip a release that has not changed

## Trigger

A freshly read release is identical to the copy kept.

## Outcome

The album's files are not read and any update it already has stays listed.
