---
kind: alternative
routes:
  web: Web
steps:
- text: The owner chooses × on a row to keep the image it has
  kind: actor
  actor: owner
  entities:
  - entity: artwork-update
    effect: reads
    facts:
    - Rows
  contexts:
    web:
      place: web::album
- text: The Product shows the row unchanged under After Apply
  kind: product
  actor: owner
  entities:
  - entity: artwork-update
    effect: reads
    facts:
    - Chosen images
  contexts:
    web:
      place: web::album
- text: The owner chooses Apply artwork
  kind: actor
  actor: owner
  entities: []
  contexts:
    web:
      place: web::album
- text: The Product writes the remaining rows
  kind: product
  actor: owner
  entities:
  - entity: album
    effect: changes
    facts:
    - Embedded artwork
  - entity: artwork-update
    effect: changes
    from: Available
    to: Applied
    facts: []
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

# Keep a row's current image

## Trigger

The owner prefers what a row carries to the suggestion for it.

## Outcome

That row is left as it is; the other rows are applied.
