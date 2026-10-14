---
kind: alternative
routes:
  web: Web
steps:
- text: The owner follows a link in the Activity feed written under an earlier identity
  kind: actor
  actor: owner
  entities:
  - entity: activity-entry
    effect: reads
    facts:
    - Album
  contexts:
    web:
      place: web::activity
- text: The Product follows the album's recorded change of identity and opens its current page
  kind: product
  actor: owner
  entities:
  - entity: album
    effect: reads
    facts:
    - Title
  contexts:
    web:
      place: web::album
---

# Open an album by an old link

## Trigger

The owner follows a link written before the album was matched or its release was merged.

## Outcome

The album's current page opens, with its whole History.

## Edge cases

- When a release is on disk twice, a link with the bare release ID lists the copies instead of choosing one.
