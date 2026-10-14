---
kind: alternative
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
- text: The Product compares the files with what a re-tag against the release would write now
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
    - Tag values
  contexts:
    web:
      place: web::album
- text: A re-tag would change an owned tag
  kind: condition
  entities: []
  contexts:
    web:
      place: web::album
- text: The Product shows the update and lists the album under Tag updates
  kind: product
  actor: owner
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
      place: web::album
---

# Open an album that has fallen behind

## Trigger

Re-tagging the album against the release now would change an owned tag.

## Outcome

The page shows the update with what would change and how far it reaches.
