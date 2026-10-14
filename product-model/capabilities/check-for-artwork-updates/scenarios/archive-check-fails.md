---
kind: edge
routes:
  web: Web
steps:
- text: The artwork check comes round while Library updates is Find updates for review
  kind: condition
  unattended: true
  entities:
  - entity: settings
    effect: reads
    facts:
    - Library updates
  contexts:
    web:
      place: web::library
- text: The Cover Art Archive does not answer
  kind: condition
  entities: []
  contexts:
    web:
      place: web::library
- text: The Product keeps the last answer and backs off before asking again
  kind: product
  entities: []
  contexts:
    web:
      place: web::library
---

# The Cover Art Archive does not answer

## Trigger

The archive fails to answer for a release.

## Outcome

The last answer is kept and the release is asked again after a back-off.
