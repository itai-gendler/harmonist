---
kind: primary
result: achieved
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
    - Tracklist changed
  contexts:
    web:
      place: web::album
  capability: apply-tag-updates
- text: The Product writes nothing and opens the track assignment editor
  kind: product
  actor: owner
  entities: []
  contexts:
    web:
      place: web::album
  capability: apply-tag-updates
- text: The owner checks each file against its track and chooses Accept changes
  kind: actor
  actor: owner
  entities:
  - entity: album
    effect: reads
    facts:
    - Tracks on disk
  contexts:
    web:
      place: web::album
  capability: edit-track-assignments
- text: The Product writes the updated tags with the accepted pairing
  kind: product
  actor: owner
  entities:
  - entity: album
    effect: changes
    facts:
    - Tag values
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
  capability: edit-track-assignments
---

# Apply a tracklist change after reviewing the pairing

## Trigger

An album's tag update changes its tracklist.

## Outcome

The update is written with the pairing the owner accepted.
