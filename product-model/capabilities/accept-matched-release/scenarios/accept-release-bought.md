---
kind: primary
routes:
  web: Web
steps:
- text: The owner ticks Don't warn me about this under Possible mismatch
  kind: actor
  actor: owner
  entities:
  - entity: album
    effect: reads
    facts:
    - Release
    - Possible mismatch
  contexts:
    web:
      place: web::album
- text: The Product records the release as the one bought
  kind: product
  actor: owner
  entities:
  - entity: album
    effect: changes
    facts:
    - Accepted release
  contexts:
    web:
      place: web::album
---

# Say the matched release is the one bought

## Trigger

The owner knows the album is the release it is matched to.

## Outcome

The possible mismatch is no longer flagged for this release.

## Edge cases

- The acceptance lapses by itself if the album is ever matched to another release.
