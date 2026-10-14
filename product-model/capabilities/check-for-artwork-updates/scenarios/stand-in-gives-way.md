---
kind: alternative
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
- text: The Product finds the release now has a front of its own
  kind: product
  entities:
  - entity: release
    effect: changes
    facts:
    - Cover art
    - Cover Art Archive checked
  contexts:
    web:
      place: web::library
- text: The album carries a stand-in for that release
  kind: condition
  entities:
  - entity: album
    effect: reads
    facts:
    - Stand-in artwork
  contexts:
    web:
      place: web::library
- text: The Product proposes replacing the stand-in rows with the release's own front
  kind: product
  entities:
  - entity: artwork-update
    effect: creates
    to: Available
    facts:
    - Kind
    - Rows
  contexts:
    web:
      place: web::library
---

# Replace a stand-in with the release's own cover

## Trigger

An album carries a cover borrowed for want of the release's own front, and the release now has one.

## Outcome

A replacement of the borrowed cover is proposed, whatever its size.
