---
kind: alternative
routes:
  web: Web
steps:
- text: A scan finds an album's files all name a different release from the one it is matched to
  kind: condition
  unattended: true
  entities:
  - entity: album
    effect: reads
    facts: []
  contexts:
    web:
      place: web::inbox
- text: The Product shows that the album's files and its record name different releases
  kind: product
  entities:
  - entity: album
    effect: changes
    from: Complete
    to: Tagging
    facts:
    - Tag values
  contexts:
    web:
      place: web::inbox
- text: The Product adopts the release the files name, keeping the album's store URL and linked purchase
  kind: product
  entities:
  - entity: album
    effect: changes
    from: Tagging
    to: Complete
    facts:
    - Release
  contexts:
    web:
      place: web::library
---

# Notice files re-tagged in another tool

## Trigger

The files of a matched album were re-tagged in another tool to a different release.

## Outcome

The album follows the files: it is matched to the release they now name, keeping its store link and purchase.

## Edge cases

- Files re-tagged to the same release are noticed by being newer than the last tagging, and the album's record catches up.
