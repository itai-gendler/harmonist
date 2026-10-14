---
kind: alternative
routes:
  web: Web
steps:
- text: The owner chooses Undo on an artwork change
  kind: actor
  actor: owner
  entities:
  - entity: artwork-change
    effect: reads
    facts:
    - Targets
  contexts:
    web:
      place: web::album
- text: A target holds something other than what the change wrote
  kind: condition
  entities:
  - entity: album
    effect: reads
    facts:
    - Embedded artwork
  contexts:
    web:
      place: web::album
- text: The Product undoes the other targets and names the one left alone
  kind: product
  actor: owner
  entities:
  - entity: album
    effect: changes
    facts:
    - Embedded artwork
  - entity: artwork-change
    effect: creates
    facts:
    - Kind
    - Targets
    - Written at
  contexts:
    web:
      place: web::album
---

# Undo artwork after a target changed

## Trigger

A track or folder cover no longer holds what the change wrote.

## Outcome

That target is left alone and named; the others are undone.
