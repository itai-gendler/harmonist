---
kind: primary
routes:
  web: Web
steps:
- text: The owner opens the album's page
  kind: actor
  actor: owner
  entities:
  - entity: album
    effect: reads
    facts:
    - Origin
    - Store URL
  contexts:
    web:
      place: web::album
- text: The Product reads every release in the album's release group
  kind: product
  actor: owner
  entities:
  - entity: release
    effect: reads
    facts:
    - Release group
    - Store links
    - Barcode
    - Media
  - entity: album
    effect: reads
    facts: []
  contexts:
    web:
      place: web::album
- text: The album's store URL or barcode belongs to another release, or the matched release's media or barcode do not fit the files
  kind: condition
  entities:
  - entity: album
    effect: reads
    facts: []
  contexts:
    web:
      place: web::album
- text: The Product lists the reasons and the releases the album could be
  kind: product
  actor: owner
  entities:
  - entity: album
    effect: changes
    facts:
    - Possible mismatch
  contexts:
    web:
      place: web::album
---

# Find a possible mismatch

## Trigger

The owner opens the page of a downloaded album or CD rip.

## Outcome

The reasons the evidence points elsewhere are listed beside the group's other releases, each with the evidence for it.

## Edge cases

- A CD rip is checked against the group's physical releases, and a download against its digital ones.
- An album whose origin is Unknown is not checked.
- Another page on the same Bandcamp store is shown as a reason to look, never as a match.
