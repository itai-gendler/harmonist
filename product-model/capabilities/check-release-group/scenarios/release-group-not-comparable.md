---
kind: edge
routes:
  web: Web
steps:
- text: The owner opens the album's page
  kind: actor
  actor: owner
  entities:
  - entity: album
    effect: reads
    facts:
    - Release
  contexts:
    web:
      place: web::album
- text: The group cannot be compared in full
  kind: condition
  entities: []
  contexts:
    web:
      place: web::album
- text: The Product says the check is incomplete and flags nothing
  kind: product
  actor: owner
  entities: []
  contexts:
    web:
      place: web::album
---

# The release group cannot be compared in full

## Trigger

The release group has more than 100 releases, a release whose media MusicBrainz has not specified, or the request fails.

## Outcome

The check says it is incomplete and makes no finding.
