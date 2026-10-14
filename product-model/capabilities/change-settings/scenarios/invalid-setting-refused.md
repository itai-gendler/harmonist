---
kind: validation
routes:
  web: Web
steps:
- text: The owner saves a setting with a value that is not allowed
  kind: actor
  actor: owner
  entities:
  - entity: settings
    effect: reads
    facts:
    - Max downloads per sync
  contexts:
    web:
      place: web::settings
- text: The Product saves nothing and says why
  kind: product
  actor: owner
  entities: []
  contexts:
    web:
      place: web::settings
---

# Save a value Harmonist cannot use

## Trigger

The owner saves a value that is not allowed, such as a negative download limit.

## Outcome

Nothing is saved and the reason is shown.
