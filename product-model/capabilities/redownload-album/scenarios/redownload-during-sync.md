---
kind: validation
routes:
  web: Web
steps:
- text: The owner chooses Re-download while a sync runs
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
- text: The Product archives nothing and says to try again when the sync finishes
  kind: product
  actor: owner
  entities: []
  contexts:
    web:
      place: web::album
---

# Re-download while a sync runs

## Trigger

A sync is already running.

## Outcome

Nothing is archived and the owner is asked to wait.
