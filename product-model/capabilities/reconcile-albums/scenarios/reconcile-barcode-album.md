---
kind: alternative
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
  contexts:
    web:
      place: web::inbox
- text: The Product searches MusicBrainz for the barcode
  kind: product
  actor: owner
  entities:
  - entity: release
    effect: reads
    facts:
    - Barcode
    - Tracklist
  contexts:
    web:
      place: web::inbox
- text: Exactly one release has the barcode
  kind: condition
  entities: []
  contexts:
    web:
      place: web::inbox
- text: The Product suggests that release, compared track by track with the files
  kind: product
  actor: owner
  entities:
  - entity: album
    effect: changes
    from: New
    to: Needs MBID
    facts:
    - Added
  - entity: suggested-match
    effect: creates
    to: Proposed
    facts:
    - Release
    - How it was found
    - Confidence
    - Track comparison
  contexts:
    web:
      place: web::inbox
---

# Adopt an album by its barcode

## Trigger

A New album's files all carry the same barcode and no release ID.

## Outcome

A single matching release is suggested for review; nothing is written to the files.
