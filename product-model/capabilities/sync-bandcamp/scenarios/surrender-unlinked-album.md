---
kind: alternative
routes:
  web: Web
steps:
- text: The owner chooses Sync Bandcamp while an album waits under Needs Linking
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
- text: The whole collection was paged and no purchase matches the album
  kind: condition
  entities:
  - entity: album
    effect: reads
    facts: []
  contexts:
    web:
      place: web::inbox
- text: The Product sends the album back to Needs MBID, keeping its release as a suggestion marked no purchase found; its files keep their tags
  kind: product
  actor: owner
  entities:
  - entity: album
    effect: changes
    from: Needs Linking
    to: Needs MBID
    facts:
    - Release
  - entity: suggested-match
    effect: creates
    to: Proposed
    facts:
    - Release
    - No purchase found
  contexts:
    web:
      place: web::inbox
---

# Return an album no purchase was found for

## Trigger

A sync that paged the whole collection found no purchase for an album waiting under Needs Linking.

## Outcome

The album returns to Needs MBID with its release kept as a read-only suggestion and a note that no purchase was found.

## Edge cases

- Only a sync that paged the whole collection gives up on an album; a partial one may simply not have seen the purchase.
