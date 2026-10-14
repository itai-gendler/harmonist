---
kind: edge
routes:
  web: Web
steps:
- text: The owner chooses Apply updates
  kind: actor
  actor: owner
  entities:
  - entity: tag-update
    effect: reads
    facts:
    - Changes
  contexts:
    web:
      place: web::album
- text: MusicBrainz no longer has the release
  kind: condition
  entities: []
  contexts:
    web:
      place: web::album
- text: The Product writes nothing and says the release is gone
  kind: product
  actor: owner
  entities: []
  contexts:
    web:
      place: web::album
---

# Apply an update to a deleted release

## Trigger

MusicBrainz deleted the album's release.

## Outcome

Nothing is written and the owner is pointed to Wrong MusicBrainz match.
