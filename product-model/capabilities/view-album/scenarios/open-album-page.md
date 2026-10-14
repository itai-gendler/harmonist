---
kind: primary
routes:
  web: Web
steps:
- text: The owner opens an album from the Library
  kind: actor
  actor: owner
  entities:
  - entity: album
    effect: reads
    facts:
    - Title
  contexts:
    web:
      place: web::library
- text: The Product re-reads the album's folders from disk
  kind: product
  actor: owner
  entities:
  - entity: album
    effect: reads
    facts:
    - Tracks on disk
    - Tag values
  contexts:
    web:
      place: web::album
- text: The Product compares the album's tags and tracks with the release, from the copy last read unless it is stale
  kind: product
  actor: owner
  entities:
  - entity: release
    effect: reads
    facts:
    - Title
    - Artist credit
    - Tracklist
    - Last read
  - entity: album
    effect: reads
    facts: []
  contexts:
    web:
      place: web::album
- text: The owner reads the album's tags beside MusicBrainz's, its tracklist and its History
  kind: actor
  actor: owner
  entities:
  - entity: album
    effect: reads
    facts:
    - Tag values
    - Tracks on disk
    - Origin
  - entity: release
    effect: reads
    facts:
    - Tracklist
  - entity: tagging
    effect: reads
    facts:
    - Field changes
    - Written at
  - entity: activity-entry
    effect: reads
    facts:
    - What happened
    - When
  contexts:
    web:
      place: web::album
---

# Open an album's page

## Trigger

The owner wants to see everything about one album.

## Outcome

The page shows the album's identity, its tags beside MusicBrainz's, its tracklist, artwork and History.

## Edge cases

- Track lengths are shown beside MusicBrainz's but never reported as something to fix.
