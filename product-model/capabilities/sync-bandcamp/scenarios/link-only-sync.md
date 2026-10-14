---
kind: primary
routes:
  web: Web
steps:
- text: The owner chooses Sync Bandcamp while albums wait under Needs Linking
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
- text: The Product pages the whole Bandcamp collection and runs the sync link-only
  kind: product
  actor: owner
  entities:
  - entity: settings
    effect: reads
    facts:
    - Bandcamp login cookies
  contexts:
    web:
      place: web::inbox
- text: The Product links each waiting album to a purchase by its purchase ID, its exact store URL, the same album slug on the same Bandcamp page, or a unique exact title among the owner's purchases
  kind: product
  actor: owner
  entities:
  - entity: album
    effect: changes
    from: Needs Linking
    to: Complete
    facts:
    - Linked purchase
    - Store URL
  - entity: bandcamp-purchase
    effect: changes
    from: To consider
    to: In library
    facts: []
  contexts:
    web:
      place: web::inbox
- text: The Activity feed says the sync finished and how many items it downloaded
  kind: condition
  entities: []
  contexts:
    web:
      place: web::activity
---

# Link purchases to albums already on disk

## Trigger

The owner chooses Sync Bandcamp while albums wait under Needs Linking.

## Outcome

Each waiting album that matches a purchase is linked to it and moves to the Library; nothing is downloaded.

## Edge cases

- A same-slug album on a different Bandcamp page is linked only when its MusicBrainz release links the purchase's URL.
- When the title cannot separate several purchases, all of them are recorded on the album as candidates and it leaves Needs Linking.
- A purchase already linked to one album is never linked to a second.
