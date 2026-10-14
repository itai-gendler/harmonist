---
kind: primary
routes:
  web: Web
steps:
- text: The owner reads No matching Bandcamp purchase on the album's card and chooses Move to Library
  kind: actor
  actor: owner
  entities:
  - entity: suggested-match
    effect: reads
    facts:
    - No purchase found
    - Release
  - entity: album
    effect: reads
    facts: []
  - entity: bandcamp-purchase
    effect: reads
    facts: []
  contexts:
    web:
      place: web::inbox
- text: The Product restores the album's release and records that it has no purchase to link
  kind: product
  actor: owner
  entities:
  - entity: album
    effect: changes
    from: Needs MBID
    to: Complete
    facts:
    - Release
    - No purchase to link
  - entity: suggested-match
    effect: changes
    from: Proposed
    to: Confirmed
    facts: []
  contexts:
    web:
      place: web::inbox
---

# Accept an album with no Bandcamp purchase

## Trigger

A full sync found no purchase for an album and sent it back to Needs MBID with its release kept read-only.

## Outcome

The album is in the Library and no later sync sends it back for a missing purchase.
