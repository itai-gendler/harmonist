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
- text: The Product reads the release's store links from MusicBrainz
  kind: product
  actor: owner
  entities:
  - entity: release
    effect: reads
    facts:
    - Store links
  contexts:
    web:
      place: web::inbox
- text: Both the files' comment and the release point to Bandcamp
  kind: condition
  entities:
  - entity: album
    effect: reads
    facts:
    - Store URL
  contexts:
    web:
      place: web::inbox
- text: The Product records the release and the store URL
  kind: product
  actor: owner
  entities:
  - entity: album
    effect: changes
    from: New
    to: Needs Linking
    facts:
    - Release
    - Store URL
    - Added
  contexts:
    web:
      place: web::inbox
---

# Adopt a tagged Bandcamp album

## Trigger

A New album carries a release ID, its comment mentions Bandcamp, and the release links to Bandcamp.

## Outcome

The album waits under Needs Linking for a sync to link its purchase.

## Edge cases

- A comment holding only the artist's Bandcamp page is still recorded; the sync can link it by title later.
