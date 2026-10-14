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
- text: An unlinked album's release group holds another release the owner bought on Bandcamp and that linked to no album
  kind: condition
  entities:
  - entity: release
    effect: reads
    facts:
    - Release group
  - entity: album
    effect: reads
    facts: []
  - entity: owner
    effect: reads
    facts: []
  contexts:
    web:
      place: web::inbox
- text: The Product suggests the owned release for the album
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
    - Owned purchase
    - Track comparison
  contexts:
    web:
      place: web::inbox
---

# Flag a possibly mis-tagged album

## Trigger

A sync leaves an album unlinked while the owner bought another release in the same release group that linked to nothing.

## Outcome

The album returns to the Inbox under Possibly mis-tagged with the owned release suggested.
