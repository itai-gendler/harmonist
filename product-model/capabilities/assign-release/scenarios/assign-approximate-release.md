---
kind: alternative
routes:
  web: Web
steps:
- text: The owner pastes a MusicBrainz release ID and chooses Assign & Tag
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
- text: The Product compares the release with the files
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
- text: The match is approximate, or the release came from a barcode or store URL lookup
  kind: condition
  entities: []
  contexts:
    web:
      place: web::inbox
- text: The Product suggests the release for review, noting how it was found
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

# Assign a release the files do not fit exactly

## Trigger

The owner assigns a release whose track count or lengths differ from the files, or chooses Use on a barcode or store URL result.

## Outcome

The release becomes a suggestion to review side by side; nothing is written.
