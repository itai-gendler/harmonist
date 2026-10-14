---
kind: edge
routes:
  web: Web
steps:
- text: The owner chooses Confirm suggestion on a review drawn earlier
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
- text: The release or the artwork no longer matches what the review showed
  kind: condition
  entities:
  - entity: release
    effect: reads
    facts:
    - Tracklist
  contexts:
    web:
      place: web::inbox
- text: The Product writes nothing and asks the owner to review the new state
  kind: product
  actor: owner
  entities: []
  contexts:
    web:
      place: web::inbox
---

# Confirm after the review went stale

## Trigger

The release or artwork changed after the review was drawn.

## Outcome

Nothing is written and the owner is asked to review again.
