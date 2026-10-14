---
kind: alternative
routes:
  web: Web
steps:
- text: The owner asks to look up the releases linked to the album's store URL
  kind: actor
  actor: owner
  entities:
  - entity: album
    effect: reads
    facts:
    - Store URL
  contexts:
    web:
      place: web::inbox
- text: The Product asks MusicBrainz afresh which releases link the URL
  kind: product
  actor: owner
  entities:
  - entity: release
    effect: reads
    facts:
    - Store links
    - Tracklist
  contexts:
    web:
      place: web::inbox
- text: Exactly one release links it
  kind: condition
  entities: []
  contexts:
    web:
      place: web::inbox
- text: The Product suggests that release, noting it was found by store URL
  kind: product
  actor: owner
  entities:
  - entity: suggested-match
    effect: creates
    to: Proposed
    facts:
    - Release
    - How it was found
    - Confidence
    - Track comparison
  contexts:
    web:
      place: web::inbox
---

# Look up the album's store URL

## Trigger

An unmatched album has a store URL recorded.

## Outcome

The one release linking that URL is suggested for review, or the releases linking it are listed.
