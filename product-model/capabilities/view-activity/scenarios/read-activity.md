---
kind: primary
routes:
  web: Web
steps:
- text: The owner opens the Activity tab
  kind: actor
  actor: owner
  entities:
  - entity: activity-entry
    effect: reads
    facts:
    - What happened
    - Album
    - When
    - Level
  contexts:
    web:
      place: web::activity
- text: The owner turns on Technical detail
  kind: actor
  actor: owner
  entities: []
  contexts:
    web:
      place: web::activity
- text: The Product shows every change each entry's action made beneath it
  kind: product
  actor: owner
  entities:
  - entity: activity-entry
    effect: reads
    facts:
    - Technical detail
  contexts:
    web:
      place: web::activity
---

# Read what Harmonist has done

## Trigger

The owner wants to know what changed.

## Outcome

Each outcome is listed with its album and time, and its technical detail when asked.

## Edge cases

- The feed pages fifty entries at a time and refreshes itself while open.
