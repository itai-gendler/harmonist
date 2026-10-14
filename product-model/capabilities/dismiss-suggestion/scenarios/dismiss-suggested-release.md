---
kind: primary
routes:
  web: Web
steps:
- text: The owner chooses Dismiss suggestion
  kind: actor
  actor: owner
  entities:
  - entity: suggested-match
    effect: reads
    facts:
    - Release
  contexts:
    web:
      place: web::inbox
- text: The Product clears the suggestion; the album stays in Needs MBID
  kind: product
  actor: owner
  entities:
  - entity: suggested-match
    effect: changes
    from: Proposed
    to: Dismissed
    facts: []
  - entity: album
    effect: reads
    facts: []
  contexts:
    web:
      place: web::inbox
- text: The album's card offers search by name, barcode or store URL and a pasted MusicBrainz ID
  kind: condition
  entities:
  - entity: album
    effect: reads
    facts:
    - Title
  contexts:
    web:
      place: web::inbox
---

# Dismiss a suggested release

## Trigger

An album has a suggestion the owner believes is wrong.

## Outcome

The suggestion is gone and the album's search tools are offered again.
