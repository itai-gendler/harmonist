---
kind: edge
routes:
  web: Web
steps:
- text: The owner asks for a barcode lookup on the album
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
- text: A suggestion for the album is already waiting for review
  kind: condition
  entities:
  - entity: suggested-match
    effect: reads
    facts:
    - Release
  - entity: album
    effect: reads
    facts: []
  contexts:
    web:
      place: web::inbox
- text: The Product answers without asking MusicBrainz and leaves the suggestion as it is
  kind: product
  actor: owner
  entities: []
  contexts:
    web:
      place: web::inbox
---

# A lookup arrives while a suggestion waits

## Trigger

A barcode or store URL lookup arrives for an album that already has a suggestion waiting.

## Outcome

The waiting suggestion is kept unchanged.
