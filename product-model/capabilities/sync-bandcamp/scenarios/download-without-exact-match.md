---
kind: alternative
routes:
  web: Web
steps:
- text: The owner chooses Sync Bandcamp with nothing waiting under Needs Linking
  kind: actor
  actor: owner
  entities: []
  contexts:
    web:
      place: web::inbox
- text: The Product downloads the new purchase
  kind: product
  actor: owner
  entities:
  - entity: album
    effect: creates
    to: Needs MBID
    facts:
    - Title
    - Artist
    - Folders
    - Tracks on disk
    - Store URL
    - Linked purchase
    - Added
  - entity: bandcamp-purchase
    effect: changes
    from: To consider
    to: In library
    facts: []
  contexts:
    web:
      place: web::inbox
- text: No release fits the download exactly and uniquely
  kind: condition
  entities: []
  contexts:
    web:
      place: web::inbox
- text: The Product leaves the download untagged, suggesting a release that fits approximately
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

# Download a purchase with no exact release

## Trigger

A downloaded purchase's store URL leads to no release, several equal releases, or an approximate fit.

## Outcome

The download waits in the Inbox under Needs MBID, with a suggestion when one release fits approximately.
