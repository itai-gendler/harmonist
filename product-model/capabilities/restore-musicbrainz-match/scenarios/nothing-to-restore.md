---
kind: validation
routes:
  web: Web
steps:
- text: The owner chooses Undo beside the cleared match
  kind: actor
  actor: owner
  entities:
  - entity: album
    effect: reads
    facts:
    - Tracks on disk
  contexts:
    web:
      place: web::album
- text: The album's files no longer all name one release
  kind: condition
  entities:
  - entity: album
    effect: reads
    facts: []
  contexts:
    web:
      place: web::album
- text: The Product says there is nothing to undo
  kind: product
  actor: owner
  entities: []
  contexts:
    web:
      place: web::album
---

# Nothing left to restore

## Trigger

The files no longer all name one release.

## Outcome

Nothing is changed and nothing is recorded.
