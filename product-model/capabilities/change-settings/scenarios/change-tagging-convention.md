---
kind: alternative
routes:
  web: Web
steps:
- text: The owner changes how titles or artist names are written and saves
  kind: actor
  actor: owner
  entities:
  - entity: settings
    effect: reads
    facts:
    - Album title
    - Standardize artist names
  contexts:
    web:
      place: web::settings
- text: The Product keeps the setting
  kind: product
  actor: owner
  entities:
  - entity: settings
    effect: changes
    facts:
    - Album title
    - Standardize artist names
  contexts:
    web:
      place: web::settings
- text: The Product re-judges the albums the change can move from the releases it keeps, without reading their files or asking MusicBrainz
  kind: product
  actor: owner
  entities:
  - entity: tag-update
    effect: creates
    to: Available
    facts:
    - Significance
    - Changes
    - Follows settings
  - entity: album
    effect: reads
    facts: []
  contexts:
    web:
      place: web::library
---

# Change a tagging convention

## Trigger

The owner changes Album title or Standardize artist names.

## Outcome

Every album whose tags do not follow the new convention shows an update labelled Settings, unannounced, and nothing is written until it is applied.

## Edge cases

- Turning a disambiguation off warns before saving that updates removing it will be pending.
- Changing the setting back withdraws the updates.
