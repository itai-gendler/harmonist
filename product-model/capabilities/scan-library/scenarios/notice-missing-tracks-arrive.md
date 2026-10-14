---
kind: alternative
routes:
  web: Web
steps:
- text: A scan finds an Incomplete album now has every track its totals call for
  kind: condition
  unattended: true
  entities:
  - entity: album
    effect: reads
    facts: []
  contexts:
    web:
      place: web::library
- text: The Product reads the album as complete
  kind: product
  entities:
  - entity: album
    effect: changes
    from: Incomplete
    to: Complete
    facts:
    - Tracks on disk
  contexts:
    web:
      place: web::library
---

# Notice missing tracks arriving

## Trigger

The tracks an Incomplete album was missing are copied into its folder.

## Outcome

The album is Complete.
