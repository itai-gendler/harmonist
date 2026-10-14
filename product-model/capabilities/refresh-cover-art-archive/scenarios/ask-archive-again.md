---
kind: primary
routes:
  web: Web
steps:
- text: The owner chooses to ask the Cover Art Archive about the release again
  kind: actor
  actor: owner
  entities:
  - entity: release
    effect: reads
    facts:
    - Cover Art Archive checked
  contexts:
    web:
      place: web::album
- text: The Product asks the archive and keeps its answer
  kind: product
  actor: owner
  entities:
  - entity: release
    effect: changes
    facts:
    - Cover art
    - Cover Art Archive checked
  contexts:
    web:
      place: web::album
- text: The archive's images would fill or improve the album's artwork
  kind: condition
  entities:
  - entity: album
    effect: reads
    facts: []
  contexts:
    web:
      place: web::album
- text: The Product proposes the artwork in the Artwork section
  kind: product
  actor: owner
  entities:
  - entity: artwork-update
    effect: creates
    to: Available
    facts:
    - Kind
    - Rows
    - Available images
  contexts:
    web:
      place: web::album
---

# Ask the archive again

## Trigger

The owner knows an image was added to the Cover Art Archive.

## Outcome

The Artwork section shows what the archive lists now and any addition or replacement it makes possible.
