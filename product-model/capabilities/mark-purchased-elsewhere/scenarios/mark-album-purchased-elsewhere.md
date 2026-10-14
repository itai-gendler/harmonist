---
kind: primary
routes:
  web: Web
steps:
- text: The owner chooses × beside the album's Bandcamp badge
  kind: actor
  actor: owner
  entities:
  - entity: album
    effect: reads
    facts:
    - Store URL
  contexts:
    web:
      place: web::inbox
- text: The Product clears the album's store URL and Bandcamp link
  kind: product
  actor: owner
  entities:
  - entity: album
    effect: changes
    from: Needs Linking
    to: Complete
    facts:
    - Store URL
    - Linked purchase
  contexts:
    web:
      place: web::inbox
---

# Mark an album as bought elsewhere

## Trigger

An album waits under Needs Linking although the owner did not buy it on Bandcamp.

## Outcome

The album leaves Needs Linking for the Library.
