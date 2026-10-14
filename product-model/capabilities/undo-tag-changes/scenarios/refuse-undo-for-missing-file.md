---
kind: validation
routes:
  web: Web
steps:
- text: The owner chooses Undo tag changes
  kind: actor
  actor: owner
  entities:
  - entity: tagging
    effect: reads
    facts:
    - Field changes
  contexts:
    web:
      place: web::album
- text: A file is missing, unreadable or ambiguous
  kind: condition
  entities:
  - entity: tagging
    effect: reads
    facts:
    - Files
  contexts:
    web:
      place: web::album
- text: The Product refuses before writing anything and says why
  kind: product
  actor: owner
  entities: []
  contexts:
    web:
      place: web::album
---

# Undo when a file cannot be found

## Trigger

A file the tagging wrote has been removed, cannot be read, or cannot be told apart from another.

## Outcome

Nothing is written.
