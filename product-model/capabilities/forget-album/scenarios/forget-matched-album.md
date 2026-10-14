---
kind: primary
routes:
  web: Web
steps:
- text: The owner chooses Forget on the album's page and confirms
  kind: actor
  actor: owner
  entities:
  - entity: album
    effect: reads
    facts:
    - Title
  contexts:
    web:
      place: web::album
- text: The Product deletes the album's record and leaves its files untouched
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
      place: web::album
- text: Automatic reconciling skips the album until the owner chooses Reconcile from tags or Harmonist restarts
  kind: condition
  entities:
  - entity: album
    effect: reads
    facts:
    - Title
  - entity: owner
    effect: reads
    facts: []
  contexts:
    web:
      place: web::inbox
---

# Forget a matched album

## Trigger

The owner wants Harmonist to start over with an album.

## Outcome

The album is back in New with its files untouched, and automatic reconciling leaves it there.
