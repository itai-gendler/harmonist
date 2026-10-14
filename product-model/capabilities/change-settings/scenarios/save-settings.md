---
kind: primary
routes:
  web: Web
steps:
- text: The owner changes settings such as Library updates, Download format or Max downloads per sync and saves
  kind: actor
  actor: owner
  entities:
  - entity: settings
    effect: reads
    facts:
    - Library updates
    - Download format
    - Max downloads per sync
  contexts:
    web:
      place: web::settings
- text: The Product checks the values, keeps them and applies them at once
  kind: product
  actor: owner
  entities:
  - entity: settings
    effect: changes
    facts:
    - Create cover.jpg in album folders
    - Album title
    - Standardize artist names
    - Always standardize multi-valued artist tags
    - Library updates
    - Download format
    - Max downloads per sync
    - MusicBrainz user agent
    - Log level
  contexts:
    web:
      place: web::settings
---

# Save the settings

## Trigger

The owner wants Harmonist to behave differently.

## Outcome

The new settings are kept and in effect at once.

## Edge cases

- Turning Library updates on takes effect on the background check's next tick, without a restart.
