---
kind: edge
routes:
  web: Web
steps:
- text: The owner chooses Accept changes on an editor drawn earlier
  kind: actor
  actor: owner
  entities: []
  contexts:
    web:
      place: web::album
- text: The files or the release no longer match what the editor showed
  kind: condition
  entities:
  - entity: album
    effect: reads
    facts:
    - Tracks on disk
  contexts:
    web:
      place: web::album
- text: The Product writes nothing and redraws the editor from what is there now
  kind: product
  actor: owner
  entities: []
  contexts:
    web:
      place: web::album
---

# Accept assignments after the files changed

## Trigger

The files or the release changed after the editor was drawn.

## Outcome

Nothing is written and the editor asks for a fresh review.
