---
kind: alternative
routes:
  web: Web
steps:
- text: The owner reads that the album's release is gone from MusicBrainz
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
- text: The owner chooses Find a new release
  kind: actor
  actor: owner
  entities: []
  contexts:
    web:
      place: web::album
- text: The Product clears the album's release
  kind: product
  actor: owner
  entities:
  - entity: album
    effect: changes
    from: Complete
    to: Needs MBID
    facts:
    - Release
  contexts:
    web:
      place: web::album
---

# Find a new release for a deleted one

## Trigger

MusicBrainz no longer has the release an album is matched to.

## Outcome

The album waits in Needs MBID for a current release.
