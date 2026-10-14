---
kind: primary
routes:
  web: Web
steps:
- text: The owner chooses Download on the potential download
  kind: actor
  actor: owner
  entities:
  - entity: bandcamp-purchase
    effect: reads
    facts:
    - Artist
    - Title
  contexts:
    web:
      place: web::inbox
- text: The Product marks the purchase for the next sync and tells the owner to sync
  kind: product
  actor: owner
  entities:
  - entity: bandcamp-purchase
    effect: changes
    from: Potential download
    to: Approved
    facts: []
  contexts:
    web:
      place: web::inbox
---

# Approve a potential download

## Trigger

A potential download waits in the Inbox.

## Outcome

The purchase downloads on the next sync.

## Edge cases

- Potential downloads and approvals last until Harmonist restarts; after a restart the next sync lists the purchase again.
