---
kind: primary
routes:
  web: Web
steps:
- text: The owner pastes a MusicBrainz release URL or ID on the album's card and chooses Assign & Tag
  kind: actor
  actor: owner
  entities:
  - entity: album
    effect: reads
    facts:
    - Title
  - entity: release
    effect: reads
    facts: []
  contexts:
    web:
      place: web::inbox
- text: The Product reads the release from MusicBrainz and compares it with the files
  kind: product
  actor: owner
  entities:
  - entity: release
    effect: reads
    facts:
    - Tracklist
  - entity: album
    effect: reads
    facts:
    - Tracks on disk
  contexts:
    web:
      place: web::inbox
- text: The files have the release's track count and every track is within four seconds of its length
  kind: condition
  entities: []
  contexts:
    web:
      place: web::inbox
- text: The Product writes the release's tags into every folder of the album and records the tagging
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
      place: web::inbox
---

# Assign a release the files fit exactly

## Trigger

The owner knows the album's release.

## Outcome

The release's tags are written into the album's files and the album moves to the Library.

## Edge cases

- A New album is assigned the same way.
- An album whose files are from Bandcamp lands in Needs Linking instead.
