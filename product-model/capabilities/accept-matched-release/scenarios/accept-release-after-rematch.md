---
kind: edge
routes:
  web: Web
steps:
- text: The owner ticks Don't warn me about this on a page drawn earlier
  kind: actor
  actor: owner
  entities:
  - entity: album
    effect: reads
    facts:
    - Release
  contexts:
    web:
      place: web::album
- text: The album is now matched to another release
  kind: condition
  entities:
  - entity: album
    effect: reads
    facts: []
  contexts:
    web:
      place: web::album
- text: The Product records nothing and asks the owner to reload the page
  kind: product
  actor: owner
  entities: []
  contexts:
    web:
      place: web::album
---

# Accept a release the album no longer has

## Trigger

The album was matched to a different release after the page was drawn.

## Outcome

Nothing is recorded and the owner is asked to reload.
