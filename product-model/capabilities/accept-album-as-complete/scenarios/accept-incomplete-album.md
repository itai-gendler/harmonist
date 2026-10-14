---
kind: primary
routes:
  web: Web
steps:
- text: The owner ticks Don't warn me about this beside the album's missing tracks
  kind: actor
  actor: owner
  entities:
  - entity: album
    effect: reads
    facts:
    - Track and disc totals
    - Tracks on disk
  contexts:
    web:
      place: web::album
- text: The Product records the acceptance and leaves the album Incomplete
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

# Stop flagging an album's missing tracks

## Trigger

An Incomplete album's missing tracks cannot be had.

## Outcome

The album is no longer listed as incomplete in the Library.
