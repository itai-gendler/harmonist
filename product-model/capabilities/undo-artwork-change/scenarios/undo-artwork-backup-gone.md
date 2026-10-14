---
kind: validation
routes:
  web: Web
steps:
- text: The owner looks for Undo on an old artwork replacement
  kind: actor
  actor: owner
  entities:
  - entity: artwork-change
    effect: reads
    facts:
    - Kind
  contexts:
    web:
      place: web::album
- text: The replaced image is no longer kept
  kind: condition
  entities: []
  contexts:
    web:
      place: web::album
- text: The Product offers no Undo for the replacement
  kind: product
  actor: owner
  entities: []
  contexts:
    web:
      place: web::album
---

# Undo a replacement whose copy is gone

## Trigger

The kept copy of a replaced image was removed to make room in the artwork store.

## Outcome

No Undo is offered for it, and an attempt says the image is no longer kept.
