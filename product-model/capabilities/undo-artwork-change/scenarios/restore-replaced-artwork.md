---
kind: primary
routes:
  web: Web
steps:
- text: The owner chooses Undo on an artwork change in the album's History
  kind: actor
  actor: owner
  entities:
  - entity: artwork-change
    effect: reads
    facts:
    - Targets
    - Written at
  - entity: album
    effect: reads
    facts: []
  contexts:
    web:
      place: web::album
- text: The Product works out the undo from the album's own records and the kept copies
  kind: product
  actor: owner
  entities:
  - entity: artwork-backup
    effect: reads
    facts:
    - Image
  - entity: album
    effect: reads
    facts: []
  contexts:
    web:
      place: web::album
- text: The Product keeps a copy of anything it overwrites, puts the replaced images back and removes the added ones
  kind: product
  actor: owner
  entities:
  - entity: artwork-backup
    effect: creates
    facts:
    - Image
    - Recent
  - entity: album
    effect: changes
    facts:
    - Embedded artwork
    - Folder cover
  - entity: artwork-change
    effect: creates
    facts:
    - Kind
    - Targets
    - Written at
  contexts:
    web:
      place: web::album
---

# Undo an artwork change

## Trigger

An artwork change put images on the album the owner does not want.

## Outcome

The replaced images are back, the added ones are gone, and the undo is in the History.

## Edge cases

- A folder cover Harmonist created is deleted again.
