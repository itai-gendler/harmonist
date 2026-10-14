---
kind: alternative
routes:
  web: Web
steps:
- text: The owner chooses Sync Bandcamp with nothing waiting under Needs Linking
  kind: actor
  actor: owner
  entities: []
  contexts:
    web:
      place: web::inbox
- text: The Product downloads new purchases in the download format, up to the per-sync limit
  kind: product
  actor: owner
  entities:
  - entity: settings
    effect: reads
    facts:
    - Download format
    - Max downloads per sync
  - entity: album
    effect: creates
    to: Needs MBID
    facts:
    - Title
    - Artist
    - Folders
    - Tracks on disk
    - Store URL
    - Linked purchase
    - Added
  - entity: bandcamp-purchase
    effect: changes
    from: To consider
    to: In library
    facts: []
  contexts:
    web:
      place: web::inbox
- text: The Product looks up the download's store URL on MusicBrainz
  kind: product
  actor: owner
  entities:
  - entity: release
    effect: reads
    facts:
    - Store links
    - Tracklist
    - Media
  contexts:
    web:
      place: web::inbox
- text: Exactly one release fits the files exactly, or one digital edition among tied ones
  kind: condition
  entities: []
  contexts:
    web:
      place: web::inbox
- text: The Product writes the release's tags into the download unasked and records the tagging
  kind: product
  actor: owner
  entities:
  - entity: album
    effect: changes
    from: Needs MBID
    to: Complete
    facts:
    - Release
    - Tag values
    - Track and disc totals
  - entity: tagging
    effect: creates
    facts:
    - Release
    - Field changes
    - Files
    - Written at
  contexts:
    web:
      place: web::library
---

# Download and tag a new purchase

## Trigger

The owner syncs with nothing waiting to be linked, and Bandcamp has a purchase not yet on disk.

## Outcome

The purchase is downloaded in the chosen format and, when its store URL leads to exactly one release the files fit exactly, tagged and listed in the Library.

## Edge cases

- Purchases past the per-sync limit wait for the next sync; approved purchases and re-downloads do not count toward it.
- Unreleased pre-orders are retried on each sync.
- A replacement for a re-downloaded album is tagged as the release it had, keeping its original Added date.
