---
kind: edge
routes:
  web: Web
steps:
- text: The owner chooses Re-download and confirms
  kind: actor
  actor: owner
  entities:
  - entity: album
    effect: reads
    facts:
    - Linked purchase
  contexts:
    web:
      place: web::album
- text: The zip cannot be written or does not match the originals
  kind: condition
  entities: []
  contexts:
    web:
      place: web::album
- text: The Product deletes nothing and reports that the album could not be archived
  kind: product
  actor: owner
  entities:
  - entity: album
    effect: reads
    facts: []
  contexts:
    web:
      place: web::album
---

# The archive cannot be made

## Trigger

The zip cannot be written or checked, for example for lack of space.

## Outcome

The album is left where it was and nothing about the purchase changes.
