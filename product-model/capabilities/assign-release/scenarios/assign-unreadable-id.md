---
kind: validation
routes:
  web: Web
steps:
- text: The owner pastes text that is not a release URL or ID and chooses Assign & Tag
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
- text: The Product says it could not read a release ID from it
  kind: product
  actor: owner
  entities: []
  contexts:
    web:
      place: web::inbox
---

# Assign something that is not a release ID

## Trigger

The owner pastes text that is neither a MusicBrainz release URL nor a 36-character ID.

## Outcome

The owner is asked for a full release URL or ID and nothing changes.
