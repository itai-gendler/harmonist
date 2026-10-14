---
kind: edge
routes:
  web: Web
steps:
- text: The owner chooses Apply artwork
  kind: actor
  actor: owner
  entities:
  - entity: artwork-update
    effect: reads
    facts:
    - Kind
  contexts:
    web:
      place: web::album
- text: An image about to be replaced cannot be kept
  kind: condition
  entities: []
  contexts:
    web:
      place: web::album
- text: The Product leaves that image alone, names it, and makes the additions
  kind: product
  actor: owner
  entities:
  - entity: album
    effect: changes
    facts:
    - Embedded artwork
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

# An image cannot be kept for Undo

## Trigger

An image to be replaced cannot be kept in the artwork store.

## Outcome

That image is left in place and named; additions are still made.
