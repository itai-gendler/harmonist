---
kind: primary
routes:
  web: Web
steps:
- text: The owner chooses Change origin on the album's page
  kind: actor
  actor: owner
  entities:
  - entity: album
    effect: reads
    facts:
    - Origin
    - Origin choice
  contexts:
    web:
      place: web::album
- text: The owner picks Bandcamp, Qobuz, Amazon, Beatport, CD or Unknown and saves
  kind: actor
  actor: owner
  entities: []
  contexts:
    web:
      place: web::album
- text: The Product records the choice in every folder of the album and clears its accepted release
  kind: product
  actor: owner
  entities:
  - entity: album
    effect: changes
    facts:
    - Origin choice
    - Origin
    - Accepted release
  contexts:
    web:
      place: web::album
---

# Choose an album's origin

## Trigger

The owner knows the files came from somewhere other than the tags suggest, such as a CD rip carrying an old download's comments.

## Outcome

The album's Origin is the owner's choice in every folder, and any earlier acceptance of its release is cleared so the new evidence is checked again.

## Edge cases

- Saving the same choice again changes nothing and keeps the accepted release.
- Unknown suppresses detection; it is a choice, not a return to detection.
