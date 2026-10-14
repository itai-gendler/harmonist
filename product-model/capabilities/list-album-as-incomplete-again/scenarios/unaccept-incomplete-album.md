---
kind: primary
routes:
  web: Web
steps:
- text: The owner unticks Don't warn me about this beside the album's missing tracks
  kind: actor
  actor: owner
  entities:
  - entity: album
    effect: reads
    facts:
    - Accepted as complete
  contexts:
    web:
      place: web::album
- text: The Product removes the acceptance
  kind: product
  actor: owner
  entities:
  - entity: album
    effect: changes
    facts:
    - Accepted as complete
  contexts:
    web:
      place: web::album
---

# Flag an album's missing tracks again

## Trigger

The owner wants an accepted album back in the Incomplete filter.

## Outcome

The album is listed as incomplete again.
