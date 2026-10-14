---
kind: primary
routes:
  web: Web
steps:
- text: The owner unticks Ignore until MusicBrainz changes
  kind: actor
  actor: owner
  entities:
  - entity: tag-update
    effect: reads
    facts:
    - Significance
  contexts:
    web:
      place: web::album
- text: The Product removes the ignore
  kind: product
  actor: owner
  entities:
  - entity: tag-update
    effect: changes
    from: Ignored
    to: Available
    facts: []
  contexts:
    web:
      place: web::album
---

# List an ignored update again

## Trigger

The owner wants an ignored update back on the list.

## Outcome

The album is listed under Tag updates again.
