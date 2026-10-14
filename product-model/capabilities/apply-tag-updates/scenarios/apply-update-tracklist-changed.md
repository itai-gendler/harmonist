---
kind: alternative
routes:
  web: Web
steps:
- text: The owner chooses Apply updates
  kind: actor
  actor: owner
  entities:
  - entity: tag-update
    effect: reads
    facts:
    - Tracklist changed
  contexts:
    web:
      place: web::album
- text: The Product writes nothing and opens the track assignment editor on the album's page
  kind: product
  actor: owner
  entities:
  - entity: album
    effect: reads
    facts:
    - Tracks on disk
  contexts:
    web:
      place: web::album
---

# Apply an update that changes the tracklist

## Trigger

The update adds, removes or renumbers tracks.

## Outcome

Nothing is written; the owner is taken to the track assignment editor to review the pairing first.
