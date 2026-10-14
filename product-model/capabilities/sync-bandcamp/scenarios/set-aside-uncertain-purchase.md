---
kind: alternative
routes:
  web: Web
steps:
- text: The owner chooses Sync Bandcamp
  kind: actor
  actor: owner
  entities: []
  contexts:
    web:
      place: web::inbox
- text: A purchase cannot be tied to an album on disk without guessing
  kind: condition
  entities:
  - entity: album
    effect: reads
    facts: []
  contexts:
    web:
      place: web::inbox
- text: The Product lists the purchase as a potential download with Download, Already in your library? and Don't download
  kind: product
  actor: owner
  entities:
  - entity: bandcamp-purchase
    effect: changes
    from: To consider
    to: Potential download
    facts:
    - Artist
    - Title
    - Purchase URL
  contexts:
    web:
      place: web::inbox
---

# Set aside a purchase that cannot be tied to an album

## Trigger

A sync meets a purchase it cannot confidently tie to an album on disk, or cannot be sure is new.

## Outcome

The purchase is not downloaded; it waits in the Inbox as a potential download.
