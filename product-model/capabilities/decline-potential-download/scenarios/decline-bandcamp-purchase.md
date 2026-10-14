---
kind: primary
routes:
  web: Web
steps:
- text: The owner chooses Don't download on the potential download
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
- text: The Product adds the purchase to the Bandcamp ignores
  kind: product
  actor: owner
  entities:
  - entity: bandcamp-purchase
    effect: changes
    from: Potential download
    to: Won't download
    facts: []
  contexts:
    web:
      place: web::inbox
---

# Decline a potential download

## Trigger

A potential download waits in the Inbox.

## Outcome

No sync downloads the purchase, and it is listed under Won't download.
