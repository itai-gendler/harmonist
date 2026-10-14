---
kind: primary
routes:
  web: Web
steps:
- text: The owner searches their library under Already in your library? on the potential download
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
- text: The Product lists albums matching the artist, title or folder
  kind: product
  actor: owner
  entities:
  - entity: album
    effect: reads
    facts:
    - Title
    - Artist
    - Folders
  contexts:
    web:
      place: web::inbox
- text: The owner chooses Link beside the album
  kind: actor
  actor: owner
  entities:
  - entity: album
    effect: reads
    facts:
    - Title
  contexts:
    web:
      place: web::inbox
- text: The Product records the purchase on the album, adopts its URL as the store URL and adds the purchase to the ignores
  kind: product
  actor: owner
  entities:
  - entity: album
    effect: changes
    facts:
    - Linked purchase
    - Store URL
  - entity: bandcamp-purchase
    effect: changes
    from: Potential download
    to: In library
    facts: []
  contexts:
    web:
      place: web::inbox
---

# Link a potential download to an album on disk

## Trigger

A potential download is an album the owner already has.

## Outcome

The album records the purchase and its URL, and no sync downloads it.
