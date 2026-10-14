---
kind: alternative
routes:
  web: Web
steps:
- text: The owner opens the Inbox while a New album waits there
  kind: actor
  actor: owner
  entities:
  - entity: album
    effect: reads
    facts:
    - Title
  contexts:
    web:
      place: web::inbox
- text: The Product records the store URL from the files' comment
  kind: product
  actor: owner
  entities:
  - entity: album
    effect: changes
    from: New
    to: Needs MBID
    facts:
    - Store URL
    - Added
  contexts:
    web:
      place: web::inbox
---

# Adopt an album with only a store URL

## Trigger

A New album's comment carries a store URL but no file carries a release ID.

## Outcome

The album waits under Needs MBID with its store URL recorded, ready for a store URL lookup.
