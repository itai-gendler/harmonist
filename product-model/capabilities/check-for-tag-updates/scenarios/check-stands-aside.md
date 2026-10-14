---
kind: edge
routes:
  web: Web
steps:
- text: Ten minutes pass while a sync or reconcile runs
  kind: condition
  unattended: true
  entities:
  - entity: settings
    effect: reads
    facts:
    - Library updates
  contexts:
    web:
      place: web::library
- text: The Product skips this pass
  kind: product
  entities: []
  contexts:
    web:
      place: web::library
---

# Stand aside for the owner's work

## Trigger

The tick comes round during a sync, a reconcile, before the library is first scanned, or while the previous pass runs.

## Outcome

Nothing is asked this tick; the albums wait for the next.
