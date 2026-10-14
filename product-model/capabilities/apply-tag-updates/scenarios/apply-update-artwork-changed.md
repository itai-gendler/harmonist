---
kind: edge
routes:
  web: Web
steps:
- text: The owner chooses Apply updates on a page drawn earlier
  kind: actor
  actor: owner
  entities:
  - entity: tag-update
    effect: reads
    facts:
    - Changes
  contexts:
    web:
      place: web::album
- text: The artwork no longer matches what the Artwork section showed
  kind: condition
  entities: []
  contexts:
    web:
      place: web::album
- text: The Product writes the tags without the artwork and says why
  kind: product
  actor: owner
  entities:
  - entity: album
    effect: changes
    facts:
    - Tag values
  - entity: tag-update
    effect: changes
    from: Available
    to: Applied
    facts: []
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

# Apply an update after the artwork changed

## Trigger

The album's artwork changed after the page drew its Artwork section.

## Outcome

The tags are written and the artwork is left alone, with the reason in the album's History.
