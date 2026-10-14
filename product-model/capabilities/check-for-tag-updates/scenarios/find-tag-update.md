---
kind: primary
routes:
  web: Web
steps:
- text: Ten minutes pass while Library updates is Find updates for review
  kind: condition
  unattended: true
  entities:
  - entity: settings
    effect: reads
    facts:
    - Library updates
  contexts:
    web:
      place: web::library
- text: The Product reads a small slice of the albums whose release has gone longest unread, skipping any read in the last week, fresh from MusicBrainz
  kind: product
  entities:
  - entity: release
    effect: changes
    facts:
    - Title
    - Artist credit
    - Tracklist
    - Barcode
    - Store links
    - Media
    - Last read
  - entity: album
    effect: reads
    facts: []
  contexts:
    web:
      place: web::library
- text: The Product compares each album's files with what a re-tag against the release would write now
  kind: product
  entities:
  - entity: album
    effect: reads
    facts:
    - Tag values
  contexts:
    web:
      place: web::library
- text: A re-tag would change an owned tag
  kind: condition
  entities: []
  contexts:
    web:
      place: web::library
- text: The Product lists the album under Tag updates and announces the update in the Activity feed when it is new and comes from MusicBrainz
  kind: product
  entities:
  - entity: tag-update
    effect: creates
    to: Available
    facts:
    - Significance
    - Changes
    - Release version
    - Follows settings
    - Tracklist changed
  - entity: album
    effect: reads
    facts: []
  contexts:
    web:
      place: web::library
---

# Find an update nobody went looking for

## Trigger

The background check's ten-minute tick comes round while Library updates is Find updates for review.

## Outcome

Albums whose tags have fallen behind MusicBrainz are listed under Tag updates, and a new update from MusicBrainz is announced in the Activity feed.

## Edge cases

- An update seen for the first time after an install, or one that only follows a tagging setting, is not announced.
- Albums are compared with MusicBrainz now, never with an earlier copy of MusicBrainz.
- With Library updates Off, nothing is asked.
