---
kind: alternative
routes:
  web: Web
steps:
- text: The owner chooses to read the release from MusicBrainz again
  kind: actor
  actor: owner
  entities:
  - entity: release
    effect: reads
    facts:
    - Last read
  contexts:
    web:
      place: web::album
- text: MusicBrainz answers with the release it was merged into
  kind: condition
  entities: []
  contexts:
    web:
      place: web::album
- text: The Product names the surviving release and offers Re-tag from merged release
  kind: product
  actor: owner
  entities:
  - entity: release
    effect: reads
    facts:
    - Title
  contexts:
    web:
      place: web::album
---

# Find the release was merged

## Trigger

MusicBrainz merged the album's release into another.

## Outcome

The page names the surviving release and offers to re-tag from it.
