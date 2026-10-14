---
kind: primary
routes:
  web: Web
steps:
- text: The owner reads each row's current image beside the one applying would write
  kind: actor
  actor: owner
  entities:
  - entity: artwork-update
    effect: reads
    facts:
    - Kind
    - Rows
  - entity: album
    effect: reads
    facts:
    - Embedded artwork
    - Folder cover
  contexts:
    web:
      place: web::album
- text: The owner chooses Apply artwork
  kind: actor
  actor: owner
  entities: []
  contexts:
    web:
      place: web::album
- text: The Product rebuilds the proposal from disk and checks it still matches what the section showed
  kind: product
  actor: owner
  entities:
  - entity: artwork-update
    effect: reads
    facts:
    - Rows
  contexts:
    web:
      place: web::album
- text: The Product keeps a copy of every image it is about to replace, then writes the images to the tracks and folder cover
  kind: product
  actor: owner
  entities:
  - entity: artwork-backup
    effect: creates
    facts:
    - Image
    - Recent
  - entity: album
    effect: changes
    facts:
    - Embedded artwork
    - Folder cover
  - entity: artwork-update
    effect: changes
    from: Available
    to: Applied
    facts: []
  - entity: artwork-change
    effect: creates
    facts:
    - Kind
    - Targets
    - Written at
  contexts:
    web:
      place: web::album
---

# Apply the artwork the section suggests

## Trigger

An album has an artwork addition or replacement waiting.

## Outcome

The album carries the images the After Apply column showed, the change is in its History, and every replaced image is kept for Undo.

## Edge cases

- Only the first picture in a file is touched; back covers and booklet pages stay.
- A compilation's folder cover comes only from the archive.
