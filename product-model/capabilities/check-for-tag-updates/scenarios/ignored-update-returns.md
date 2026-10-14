---
kind: alternative
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
- text: The Product reads an album's release fresh from MusicBrainz
  kind: product
  entities:
  - entity: release
    effect: changes
    facts:
    - Tracklist
    - Last read
  - entity: album
    effect: reads
    facts: []
  contexts:
    web:
      place: web::library
- text: The release is a different version from the one the update was ignored against
  kind: condition
  entities: []
  contexts:
    web:
      place: web::library
- text: The Product lists the album's update again
  kind: product
  entities:
  - entity: tag-update
    effect: changes
    from: Ignored
    to: Available
    facts:
    - Release version
    - Changes
  - entity: album
    effect: reads
    facts: []
  contexts:
    web:
      place: web::library
---

# List an ignored update again when MusicBrainz changes

## Trigger

The owner ignored an album's update and the release then changed on MusicBrainz.

## Outcome

The album's update is listed again.
