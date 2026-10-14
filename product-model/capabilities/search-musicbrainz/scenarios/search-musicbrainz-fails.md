---
kind: edge
routes:
  web: Web
steps:
- text: The owner searches for the album's release
  kind: actor
  actor: owner
  entities:
  - entity: album
    effect: reads
    facts:
    - Title
  contexts:
    web:
      place: web::inbox
- text: MusicBrainz does not answer
  kind: condition
  entities: []
  contexts:
    web:
      place: web::inbox
- text: The Product shows that the search failed, and the album stays as it was
  kind: product
  actor: owner
  entities:
  - entity: album
    effect: reads
    facts: []
  contexts:
    web:
      place: web::inbox
---

# MusicBrainz cannot be reached

## Trigger

The owner searches or looks up while MusicBrainz fails to answer.

## Outcome

The failure is shown beside the search tools and nothing changes.
