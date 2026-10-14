---
kind: primary
routes:
  web: Web
steps:
- text: The owner chooses Restore beside the purchase under Won't download in Settings
  kind: actor
  actor: owner
  entities:
  - entity: bandcamp-purchase
    effect: reads
    facts:
    - Artist
    - Title
  - entity: settings
    effect: reads
    facts: []
  contexts:
    web:
      place: web::settings
- text: The Product takes the purchase out of the owner's ignores
  kind: product
  actor: owner
  entities:
  - entity: bandcamp-purchase
    effect: changes
    from: Won't download
    to: To consider
    facts: []
  contexts:
    web:
      place: web::settings
---

# Restore a purchase from Won't download

## Trigger

The owner changes their mind about a declined purchase.

## Outcome

The next sync considers the purchase again, offering or downloading it as its mode allows.

## Edge cases

- Only purchases the owner declined are restored; purchases recorded as already downloaded stay ignored.
