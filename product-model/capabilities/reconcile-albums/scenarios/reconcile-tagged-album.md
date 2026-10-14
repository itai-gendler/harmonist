---
kind: primary
routes:
  web: Web
steps:
- text: The owner opens the Inbox while a New album waits there
  kind: actor
  actor: owner
  entities:
  - entity: album
    effect: reads
    facts:
    - Title
    - Artist
  contexts:
    web:
      place: web::inbox
- text: The Product starts reconciling every New album whose files carry a release ID or a barcode
  kind: product
  actor: owner
  entities:
  - entity: album
    effect: reads
    facts: []
  contexts:
    web:
      place: web::inbox
- text: The Product records the release the album's files name as its match
  kind: product
  actor: owner
  entities:
  - entity: album
    effect: changes
    from: New
    to: Complete
    facts:
    - Release
    - Added
  contexts:
    web:
      place: web::inbox
---

# Adopt an album already tagged with its release

## Trigger

The owner opens the Inbox while a New album's files carry a MusicBrainz release ID.

## Outcome

The album is matched to the release its files name and moves to the Library; its files are not rewritten.

## Edge cases

- An album the owner chose to Forget is skipped until the owner chooses Reconcile from tags or Harmonist restarts.
