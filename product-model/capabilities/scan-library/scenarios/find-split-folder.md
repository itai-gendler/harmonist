---
kind: alternative
routes:
  web: Web
steps:
- text: A scan reads a folder that was Inconsistent and whose files now agree
  kind: condition
  unattended: true
  entities: []
  contexts:
    web:
      place: web::inbox
- text: The Product treats the folder as an album of its own
  kind: product
  entities:
  - entity: album
    effect: changes
    from: Inconsistent
    to: New
    facts:
    - Title
    - Artist
    - Tracks on disk
  contexts:
    web:
      place: web::inbox
---

# Find a folder that was split

## Trigger

An Inconsistent folder has been split into separate folders outside Harmonist.

## Outcome

Each folder is now an album of its own.
