---
kind: validation
routes:
  web: Web
steps:
- text: The owner asks to ignore an update whose changes only follow their own spelling choices
  kind: actor
  actor: owner
  entities:
  - entity: tag-update
    effect: reads
    facts:
    - Significance
    - Follows settings
  contexts:
    web:
      place: web::album
- text: The Product refuses and points to the spelling option that causes it
  kind: product
  actor: owner
  entities: []
  contexts:
    web:
      place: web::album
---

# Ignore an update that only follows the settings

## Trigger

The album's only changes bring it into line with a tagging setting.

## Outcome

Nothing is ignored; the remedy is the setting.
