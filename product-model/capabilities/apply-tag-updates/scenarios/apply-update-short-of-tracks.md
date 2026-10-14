---
kind: alternative
routes:
  web: Web
steps:
- text: The owner chooses Apply updates
  kind: actor
  actor: owner
  entities:
  - entity: tag-update
    effect: reads
    facts:
    - Changes
  contexts:
    web:
      place: web::album
- text: The Product refuses to write, showing how many tracks MusicBrainz lists and how many are here
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
      place: web::album
- text: The owner chooses Re-tag as incomplete
  kind: actor
  actor: owner
  entities: []
  contexts:
    web:
      place: web::album
- text: The Product writes the release's tags and totals into the files present
  kind: product
  actor: owner
  entities:
  - entity: album
    effect: changes
    from: Complete
    to: Incomplete
    facts:
    - Tag values
    - Track and disc totals
  - entity: tag-update
    effect: changes
    from: Available
    to: Applied
    facts: []
  - entity: tagging
    effect: creates
    facts:
    - Release
    - Field changes
    - Files
    - Written at
  contexts:
    web:
      place: web::album
---

# Apply an update that lists more tracks than the files

## Trigger

MusicBrainz now lists more tracks for the release than the album has.

## Outcome

Nothing is written until the owner chooses Re-tag as incomplete; then the files get the new tags and the album is listed as Incomplete.
