---
kind: edge
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
- text: Bandcamp cannot be synced
  kind: condition
  entities: []
  contexts:
    web:
      place: web::inbox
- text: The Product reports in the Activity feed that the sync failed and why
  kind: product
  actor: owner
  entities: []
  contexts:
    web:
      place: web::activity
---

# The sync fails

## Trigger

Bandcamp refuses the login or the sync breaks off.

## Outcome

The Activity feed reports the failure and its reason.
