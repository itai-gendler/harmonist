---
kind: edge
routes:
  web: Web
steps:
- text: The owner opens the album's page
  kind: actor
  actor: owner
  entities:
  - entity: album
    effect: reads
    facts:
    - Title
  contexts:
    web:
      place: web::library
- text: MusicBrainz says the release no longer exists
  kind: condition
  entities: []
  contexts:
    web:
      place: web::album
- text: The Product says the release is gone and offers Find a new release
  kind: product
  actor: owner
  entities:
  - entity: album
    effect: reads
    facts:
    - Release
  contexts:
    web:
      place: web::album
---

# Open an album whose release was deleted

## Trigger

MusicBrainz no longer has the album's release.

## Outcome

The page says so and offers Find a new release.
