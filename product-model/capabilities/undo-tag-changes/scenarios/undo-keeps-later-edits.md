---
kind: alternative
routes:
  web: Web
steps:
- text: The owner chooses Undo tag changes on an older tagging
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
- text: Some fields no longer carry what the tagging wrote
  kind: condition
  entities:
  - entity: album
    effect: reads
    facts:
    - Tag values
  - entity: tagging
    effect: reads
    facts: []
  contexts:
    web:
      place: web::album
- text: The Product puts back the other fields and names the ones left alone
  kind: product
  actor: owner
  entities:
  - entity: album
    effect: changes
    facts:
    - Tag values
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

# Undo a tagging after some fields changed again

## Trigger

Some fields were changed after the tagging, in another tool or by a later update.

## Outcome

Those fields are kept and named in the result; the rest are put back.
