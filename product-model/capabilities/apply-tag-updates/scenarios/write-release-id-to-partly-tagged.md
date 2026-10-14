---
kind: alternative
routes:
  web: Web
steps:
- text: The owner chooses Write it to those files beside the warning that some files lack the release ID
  kind: actor
  actor: owner
  entities:
  - entity: album
    effect: reads
    facts:
    - Tracks on disk
  contexts:
    web:
      place: web::album
- text: The Product re-tags the album from the release
  kind: product
  actor: owner
  entities:
  - entity: album
    effect: changes
    facts:
    - Tag values
  - entity: tagging
    effect: creates
    facts:
    - Release
    - Field changes
    - Files
    - Written at
  contexts:
    web:
      place: web::album
---

# Write the release ID to files missing it

## Trigger

Some of the album's files lack the matched release's MusicBrainz ID.

## Outcome

Every file carries the release ID, and the album leaves the Partially tagged filter.
