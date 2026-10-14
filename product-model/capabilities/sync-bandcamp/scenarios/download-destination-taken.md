---
kind: edge
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
- text: The folder a purchase would download into is not empty and its records do not identify that exact purchase
  kind: condition
  entities: []
  contexts:
    web:
      place: web::inbox
- text: The Product leaves the purchase undownloaded as a potential download and reports the conflict
  kind: product
  actor: owner
  entities:
  - entity: bandcamp-purchase
    effect: changes
    from: To consider
    to: Potential download
    facts:
    - Artist
    - Title
    - Purchase URL
  contexts:
    web:
      place: web::inbox
---

# A download's folder is already taken

## Trigger

A new purchase's download folder holds files that do not prove they are that purchase.

## Outcome

The purchase stays pending with the conflict reported, and nothing is mixed into the folder.

## Edge cases

- Approving the download does not override the conflict; the owner moves the older copy or links the purchase to it.
