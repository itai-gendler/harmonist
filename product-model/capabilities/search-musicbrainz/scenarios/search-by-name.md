---
kind: primary
routes:
  web: Web
steps:
- text: The owner enters an artist and album title on the album's card and searches
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
- text: The Product searches MusicBrainz and lists up to five releases, marking any whose store link or barcode matches the files
  kind: product
  actor: owner
  entities:
  - entity: release
    effect: reads
    facts:
    - Title
    - Artist credit
    - Tracklist
    - Media
    - Store links
    - Barcode
  contexts:
    web:
      place: web::inbox
- text: The owner compares the listed releases with the album's files
  kind: actor
  actor: owner
  entities:
  - entity: release
    effect: reads
    facts:
    - Title
    - Tracklist
  - entity: album
    effect: reads
    facts:
    - Tracks on disk
  contexts:
    web:
      place: web::inbox
---

# Search by artist and title

## Trigger

An album in New or Needs MBID has no suggestion waiting.

## Outcome

Up to five releases are listed, each with its track count, media and evidence, ready to use.

## Edge cases

- A release missing from MusicBrainz can be added through Harmony, after which a search finds it.
