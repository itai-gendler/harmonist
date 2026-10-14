---
kind: primary
routes:
  web: Web
steps:
- text: Files change in the music folder, or the hourly rescan runs
  kind: condition
  unattended: true
  entities: []
  contexts:
    web:
      place: web::inbox
- text: The Product reads the tags of a folder it has no record for and finds one album whose files agree
  kind: product
  entities:
  - entity: album
    effect: creates
    to: New
    facts:
    - Title
    - Artist
    - Folders
    - Tracks on disk
    - Added
  contexts:
    web:
      place: web::inbox
- text: The album waits in the Inbox under New
  kind: condition
  entities:
  - entity: album
    effect: reads
    facts:
    - Title
    - Artist
  contexts:
    web:
      place: web::inbox
---

# Find a new album folder

## Trigger

Files change in the music folder, or the hourly rescan runs.

## Outcome

A new album appears in the Inbox under New, with nothing on disk changed.

## Edge cases

- Folders tagged with the same release and holding different tracks of it are read as one album.
- Two copies of one release on disk are two albums, each identified by where it lives.
- A scan the owner started locks the Inbox while it rebuilds; a timed rescan does not.
- The hourly rescan never runs during a sync or a reconcile.
