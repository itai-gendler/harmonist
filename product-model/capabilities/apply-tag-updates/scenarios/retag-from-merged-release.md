---
kind: alternative
routes:
  web: Web
steps:
- text: The owner chooses Re-tag from merged release
  kind: actor
  actor: owner
  entities:
  - entity: release
    effect: reads
    facts:
    - Title
  contexts:
    web:
      place: web::album
- text: The Product writes the surviving release's tags, its ID included, and moves the album's record to it
  kind: product
  actor: owner
  entities:
  - entity: album
    effect: changes
    facts:
    - Release
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

# Re-tag from the release it was merged into

## Trigger

MusicBrainz merged the album's release into another.

## Outcome

The album's files and record carry the surviving release.

## Edge cases

- The album's History and old links follow it to the new release.
