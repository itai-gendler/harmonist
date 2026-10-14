---
kind: alternative
routes:
  web: Web
steps:
- text: The owner asks to look up the barcode the album's files share
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
- text: The Product retrieves every release with exactly that barcode
  kind: product
  actor: owner
  entities:
  - entity: release
    effect: reads
    facts:
    - Barcode
    - Tracklist
    - Media
    - Store links
  contexts:
    web:
      place: web::inbox
- text: Exactly one release fits, or a known Qobuz origin narrows a small complete set to one digital release with the files' track count
  kind: condition
  entities: []
  contexts:
    web:
      place: web::inbox
- text: The Product suggests that release, noting it was found by barcode
  kind: product
  actor: owner
  entities:
  - entity: suggested-match
    effect: creates
    to: Proposed
    facts:
    - Release
    - How it was found
    - Confidence
    - Track comparison
  contexts:
    web:
      place: web::inbox
---

# Look up the album's barcode

## Trigger

An unmatched album's files all carry the same barcode.

## Outcome

One compatible release is suggested for review, or every exact match is listed to choose from.

## Edge cases

- Barcodes are compared in their 14-digit form.
- Without one compatible release, every result is listed as a choice.
