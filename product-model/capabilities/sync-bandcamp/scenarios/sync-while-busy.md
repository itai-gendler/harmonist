---
kind: validation
routes:
  web: Web
steps:
- text: The owner chooses Sync Bandcamp
  kind: actor
  actor: owner
  entities: []
  contexts:
    web:
      place: web::inbox
- text: A reconcile, the first scan of the library, or another sync is still running
  kind: condition
  entities: []
  contexts:
    web:
      place: web::inbox
- text: The Product starts nothing and says to try again when it finishes
  kind: product
  actor: owner
  entities: []
  contexts:
    web:
      place: web::inbox
---

# Sync while Harmonist is busy

## Trigger

The owner chooses Sync Bandcamp while albums are being reconciled, while the first scan is still running, or while a sync runs.

## Outcome

No sync starts and the owner is told why.
