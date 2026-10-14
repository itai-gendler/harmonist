---
kind: alternative
routes:
  web: Web
steps:
- text: The owner chooses Use beside a release the name search listed
  kind: actor
  actor: owner
  entities:
  - entity: release
    effect: reads
    facts:
    - Title
    - Tracklist
  contexts:
    web:
      place: web::inbox
- text: The Product compares the release with the files
  kind: product
  actor: owner
  entities:
  - entity: album
    effect: reads
    facts:
    - Tracks on disk
  contexts:
    web:
      place: web::inbox
- text: The files fit the release exactly
  kind: condition
  entities: []
  contexts:
    web:
      place: web::inbox
- text: The Product writes the release's tags into the album's files and records the tagging
  kind: product
  actor: owner
  entities:
  - entity: album
    effect: changes
    from: Needs MBID
    to: Complete
    facts:
    - Release
    - Tag values
    - Track and disc totals
  - entity: tagging
    effect: creates
    facts:
    - Release
    - Field changes
    - Files
    - Written at
  contexts:
    web:
      place: web::inbox
---

# Use a release from a name search

## Trigger

A name search listed the album's release.

## Outcome

When the files fit exactly, the album is tagged as that release.
