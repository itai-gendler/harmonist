---
kind: primary
routes:
  web: Web
steps:
- text: The artwork check comes round while Library updates is Find updates for review
  kind: condition
  unattended: true
  entities:
  - entity: settings
    effect: reads
    facts:
    - Library updates
  contexts:
    web:
      place: web::library
- text: The Product asks the Cover Art Archive about the releases checked longest ago
  kind: product
  entities:
  - entity: release
    effect: changes
    facts:
    - Cover art
    - Cover Art Archive checked
  contexts:
    web:
      place: web::library
- text: The Product weighs the archive's front against what each album's tracks and folder cover carry
  kind: product
  entities:
  - entity: album
    effect: reads
    facts:
    - Embedded artwork
    - Folder cover
  contexts:
    web:
      place: web::library
- text: A track has no artwork, a folder cover is missing and Create cover.jpg in album folders is Only when missing, or the archive's front is larger than the folder cover
  kind: condition
  entities:
  - entity: album
    effect: reads
    facts: []
  contexts:
    web:
      place: web::library
- text: The Product lists the album under Artwork updates
  kind: product
  entities:
  - entity: artwork-update
    effect: creates
    to: Available
    facts:
    - Kind
    - Rows
    - Available images
  - entity: album
    effect: reads
    facts: []
  contexts:
    web:
      place: web::library
---

# Find artwork an album could use

## Trigger

The background artwork check comes round while Library updates is Find updates for review.

## Outcome

Albums whose artwork could be filled or improved are listed under Artwork updates as an Addition or a Replacement.

## Edge cases

- A larger folder cover proposes nothing for the tracks; tracks carrying different images keep them.
- Unchecked or unreadable artwork is never a claim that nothing is needed.
- Ignoring a tag update does not hide an artwork update.
