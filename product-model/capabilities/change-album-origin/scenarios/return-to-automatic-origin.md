---
kind: alternative
routes:
  web: Web
steps:
- text: The owner chooses Automatic detection and saves
  kind: actor
  actor: owner
  entities:
  - entity: album
    effect: reads
    facts:
    - Origin choice
  contexts:
    web:
      place: web::album
- text: The Product removes the choice from every folder and clears the accepted release
  kind: product
  actor: owner
  entities:
  - entity: album
    effect: changes
    facts:
    - Origin choice
    - Origin
    - Accepted release
  contexts:
    web:
      place: web::album
---

# Return to automatic detection

## Trigger

The owner wants the album's tags to decide its origin again.

## Outcome

The album's Origin is deduced from its tags again.
