---
kind: primary
routes:
  web: Web
steps:
- text: The owner unticks Don't warn me about this
  kind: actor
  actor: owner
  entities:
  - entity: album
    effect: reads
    facts:
    - Accepted release
  contexts:
    web:
      place: web::album
- text: The Product removes the acceptance
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

# Turn the mismatch warning back on

## Trigger

The owner is no longer sure the matched release is the one bought.

## Outcome

The album can be flagged as a possible mismatch again.
