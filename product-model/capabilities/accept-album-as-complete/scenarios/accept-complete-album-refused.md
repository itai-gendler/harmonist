---
kind: validation
routes:
  web: Web
steps:
- text: The owner asks to accept an album that has every track
  kind: actor
  actor: owner
  entities:
  - entity: album
    effect: reads
    facts:
    - Track and disc totals
  contexts:
    web:
      place: web::album
- text: 'The Product refuses: only an incomplete album can be accepted as complete'
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

# Accept an album that is not incomplete

## Trigger

The request concerns an album that is not Incomplete.

## Outcome

Nothing is recorded.
