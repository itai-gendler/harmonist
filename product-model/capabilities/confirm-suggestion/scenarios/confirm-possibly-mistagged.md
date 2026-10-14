---
kind: alternative
routes:
  web: Web
steps:
- text: The owner reviews an album under Possibly mis-tagged
  kind: actor
  actor: owner
  entities:
  - entity: suggested-match
    effect: reads
    facts:
    - Release
    - Owned purchase
    - Track comparison
  - entity: album
    effect: reads
    facts: []
  contexts:
    web:
      place: web::inbox
- text: The owner chooses Confirm suggestion
  kind: actor
  actor: owner
  entities:
  - entity: suggested-match
    effect: reads
    facts:
    - Release
  contexts:
    web:
      place: web::inbox
- text: The Product writes the owned release's tags, records the purchase's URL as the store URL and clears the matching potential download
  kind: product
  actor: owner
  entities:
  - entity: album
    effect: changes
    from: Needs MBID
    to: Needs Linking
    facts:
    - Release
    - Tag values
    - Track and disc totals
    - Store URL
  - entity: suggested-match
    effect: changes
    from: Proposed
    to: Confirmed
    facts: []
  - entity: bandcamp-purchase
    effect: changes
    from: Potential download
    to: To consider
    facts: []
  - entity: tagging
    effect: creates
    facts:
    - Release
    - Field changes
    - Files
    - Written at
  contexts:
    web:
      place: web::inbox
---

# Confirm a possibly mis-tagged album

## Trigger

A sync found the owner bought another release in the album's release group, and suggested it.

## Outcome

The album is tagged as the release the owner bought, its store URL becomes that purchase's, and the matching potential download is cleared for the next sync to link.
