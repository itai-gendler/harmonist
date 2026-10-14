---
kind: alternative
routes:
  web: Web
steps:
- text: The owner chooses Reconcile from tags on the album's card
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
- text: The Product records the release the album's files name as its match
  kind: product
  actor: owner
  entities:
  - entity: album
    effect: changes
    from: New
    to: Complete
    facts:
    - Release
    - Added
  contexts:
    web:
      place: web::inbox
---

# Reconcile one album from its tags

## Trigger

The owner chooses Reconcile from tags on a New album whose files carry a release ID.

## Outcome

The album is matched to the release its files name, even if the owner had earlier chosen Forget.

## Edge cases

- An album already reconciled reports Already reconciled.
- Files with no release ID report that there is nothing to reconcile from.
