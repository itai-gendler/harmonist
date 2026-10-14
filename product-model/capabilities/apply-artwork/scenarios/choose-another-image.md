---
kind: alternative
routes:
  web: Web
steps:
- text: The owner steps through the archive's images for a row, narrowing to Front only or going on to Other releases
  kind: actor
  actor: owner
  entities:
  - entity: artwork-update
    effect: reads
    facts:
    - Available images
  contexts:
    web:
      place: web::album
- text: The owner chooses Use for the row
  kind: actor
  actor: owner
  entities:
  - entity: artwork-update
    effect: reads
    facts:
    - Rows
  contexts:
    web:
      place: web::album
- text: The Product fetches the original image and shows it under After Apply for that row only
  kind: product
  actor: owner
  entities:
  - entity: artwork-update
    effect: reads
    facts:
    - Chosen images
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
- text: The Product writes the chosen image to that row's places
  kind: product
  actor: owner
  entities:
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

# Choose another image for a row

## Trigger

The suggested image is the wrong scan, crop or pressing.

## Outcome

The chosen image reaches only its own row, and is written when the owner applies.

## Edge cases

- Choosing the image a row already carries shows it as Unchanged.
- Matrix, raw and watermarked images are never offered.
