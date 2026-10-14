---
kind: primary
routes:
  web: Web
steps:
- text: The owner chooses Re-download on the album's page and confirms the download format
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
- text: The Product zips every folder of the album into the top of the music folder and checks every file in the zip against the original
  kind: product
  actor: owner
  entities:
  - entity: settings
    effect: reads
    facts:
    - Download format
  - entity: album
    effect: reads
    facts: []
  contexts:
    web:
      place: web::album
- text: The Product removes the album's folders, approves the purchase for download and starts a sync
  kind: product
  actor: owner
  entities:
  - entity: album
    effect: removes
    from: Complete
  - entity: bandcamp-purchase
    effect: changes
    from: In library
    to: Approved
    facts: []
  contexts:
    web:
      place: web::album
- text: The Inbox shows the album as re-downloading until the replacement arrives
  kind: condition
  entities:
  - entity: album
    effect: reads
    facts: []
  contexts:
    web:
      place: web::inbox
---

# Re-download an album linked to its purchase

## Trigger

An album linked to exactly one Bandcamp purchase should be fetched again.

## Outcome

The old files are in a checked zip in the music folder, the album has left the library while the sync fetches it again, and the Inbox shows it as being re-downloaded.

## Edge cases

- Nothing ever deletes the zip; unzipping it restores the album exactly.
- An album that was Incomplete may come back incomplete; a complete album that comes back short lands in Needs MBID.
