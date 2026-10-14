---
kind: alternative
routes:
  web: Web
steps:
- text: The owner chooses Link beside the purchase the album's card suggests
  kind: actor
  actor: owner
  entities:
  - entity: bandcamp-purchase
    effect: reads
    facts:
    - Artist
    - Title
  - entity: album
    effect: reads
    facts:
    - Title
  contexts:
    web:
      place: web::inbox
- text: The Product records the purchase on the album and adds it to the ignores
  kind: product
  actor: owner
  entities:
  - entity: album
    effect: changes
    from: Needs Linking
    to: Complete
    facts:
    - Linked purchase
    - Store URL
  - entity: bandcamp-purchase
    effect: changes
    from: Potential download
    to: In library
    facts: []
  contexts:
    web:
      place: web::inbox
---

# Link the purchase an unlinked album suggests

## Trigger

An album under Needs Linking, or one a sync found no purchase for, has a potential download that probably is it.

## Outcome

The album is linked to the purchase and moves to the Library.
