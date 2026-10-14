---
kind: edge
routes:
  web: Web
steps:
- text: The owner chooses Apply artwork on a section drawn earlier
  kind: actor
  actor: owner
  entities: []
  contexts:
    web:
      place: web::album
- text: The proposal rebuilt from disk differs from what the section showed
  kind: condition
  entities:
  - entity: artwork-update
    effect: reads
    facts:
    - Rows
  contexts:
    web:
      place: web::album
- text: The Product writes nothing and redraws the section from what is there now
  kind: product
  actor: owner
  entities: []
  contexts:
    web:
      place: web::album
---

# Apply artwork after it changed

## Trigger

An image changed, or a new archive image arrived, after the section was drawn.

## Outcome

Nothing is written and the section is drawn again to be looked at.
