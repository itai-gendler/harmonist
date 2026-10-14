---
kind: edge
routes:
  web: Web
steps:
- text: A scan reads a folder whose files name different releases, or whose untagged files disagree on the album title
  kind: condition
  unattended: true
  entities:
  - entity: album
    effect: reads
    facts: []
  contexts:
    web:
      place: web::inbox
- text: The Product records the folder as one album that cannot be matched
  kind: product
  entities:
  - entity: album
    effect: creates
    to: Inconsistent
    facts:
    - Title
    - Folders
    - Tracks on disk
    - Added
  contexts:
    web:
      place: web::inbox
- text: The album waits in the Inbox under Inconsistent with no action but splitting the folder
  kind: condition
  entities:
  - entity: album
    effect: reads
    facts:
    - Folders
  contexts:
    web:
      place: web::inbox
---

# Find a folder whose files disagree

## Trigger

A scan reads a folder whose files disagree about which album they belong to.

## Outcome

The folder is shown under Inconsistent until it is split.
