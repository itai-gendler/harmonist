---
kind: primary
routes:
  web: Web
steps:
- text: The owner chooses Erase sidecars under Maintenance and confirms
  kind: actor
  actor: owner
  entities: []
  contexts:
    web:
      place: web::settings
- text: The Product deletes the record in every album folder and resets where the last Bandcamp sync left off
  kind: product
  actor: owner
  entities:
  - entity: album
    effect: changes
    from: Complete
    to: New
    facts:
    - Release
    - Store URL
    - Linked purchase
    - Origin choice
    - Accepted as complete
    - Accepted release
    - No purchase to link
  contexts:
    web:
      place: web::settings
- text: The Product rescans the library and warns in the Activity feed how many records it erased
  kind: product
  actor: owner
  entities: []
  contexts:
    web:
      place: web::inbox
---

# Erase every album record

## Trigger

The owner wants to start fresh or remove Harmonist.

## Outcome

Every album record is gone, the files are untouched, the next Bandcamp sync pages the whole collection, and the library is rescanned from its tags.

## Edge cases

- The Bandcamp ignores are kept, so nothing already downloaded is fetched again.
- Opening the Inbox afterwards reconciles albums from their tags again.
