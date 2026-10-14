---
kind: primary
routes:
  web: Web
steps:
- text: The owner opens the suggested match on the album's card
  kind: actor
  actor: owner
  entities:
  - entity: suggested-match
    effect: reads
    facts:
    - Release
    - How it was found
    - Confidence
    - Track comparison
  - entity: album
    effect: reads
    facts: []
  contexts:
    web:
      place: web::inbox
- text: The Product shows the files beside the release's tracks and the tag changes and artwork confirming would write
  kind: product
  actor: owner
  entities:
  - entity: release
    effect: reads
    facts:
    - Tracklist
  - entity: album
    effect: reads
    facts:
    - Tracks on disk
  - entity: tag-update
    effect: reads
    facts:
    - Changes
  - entity: artwork-update
    effect: reads
    facts:
    - Rows
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
- text: The Product checks the release and artwork are still what the review showed
  kind: product
  actor: owner
  entities:
  - entity: release
    effect: reads
    facts:
    - Tracklist
  contexts:
    web:
      place: web::inbox
- text: The Product writes the release's tags into every folder of the album and records the tagging
  kind: product
  actor: owner
  entities:
  - entity: album
    effect: changes
    from: Needs MBID
    to: Complete
    facts:
    - Release
    - Tag values
    - Track and disc totals
  - entity: suggested-match
    effect: changes
    from: Proposed
    to: Confirmed
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

# Confirm a suggested release

## Trigger

An album in Needs MBID has a suggested match waiting.

## Outcome

The album is tagged as the suggested release, its History records the match and how it was found, and it moves to the Library.

## Edge cases

- Reviewed artwork, replacements included, is written with the tags; an image that cannot be kept for Undo is left alone and named.
- An album whose files are from Bandcamp lands in Needs Linking instead.
- Confirming on the album's page reopens the page under the album's new identity.
