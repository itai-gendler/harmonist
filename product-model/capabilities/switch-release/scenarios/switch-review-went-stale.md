---
kind: edge
routes:
  web: Web
steps:
- text: The owner confirms a switch reviewed earlier
  kind: actor
  actor: owner
  entities: []
  contexts:
    web:
      place: web::album
- text: The album is no longer matched to the release the review started from
  kind: condition
  entities:
  - entity: album
    effect: reads
    facts:
    - Release
  contexts:
    web:
      place: web::album
- text: The Product writes nothing and asks the owner to choose again
  kind: product
  actor: owner
  entities: []
  contexts:
    web:
      place: web::album
---

# Switch after the review went stale

## Trigger

The album's release changed after the review was drawn.

## Outcome

Nothing is written and the owner is asked to close the review and choose again.
