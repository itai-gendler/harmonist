---
kind: primary
result: achieved
routes:
  web: Web
steps:
- text: The owner chooses Dismiss suggestion on the album's page
  kind: actor
  actor: owner
  entities:
  - entity: suggested-match
    effect: reads
    facts:
    - Release
  - entity: album
    effect: reads
    facts: []
  contexts:
    web:
      place: web::album
  capability: dismiss-suggestion
- text: The Product clears the suggestion and reopens the album's page with the name search forward
  kind: product
  actor: owner
  entities:
  - entity: suggested-match
    effect: changes
    from: Proposed
    to: Dismissed
    facts: []
  - entity: album
    effect: reads
    facts: []
  contexts:
    web:
      place: web::album
  capability: dismiss-suggestion
- text: The owner enters an artist and album title and searches
  kind: actor
  actor: owner
  entities:
  - entity: album
    effect: reads
    facts:
    - Title
    - Artist
  contexts:
    web:
      place: web::album
  capability: search-musicbrainz
- text: The Product lists the matching releases
  kind: product
  actor: owner
  entities:
  - entity: release
    effect: reads
    facts:
    - Title
    - Tracklist
    - Media
  contexts:
    web:
      place: web::album
  capability: search-musicbrainz
---

# Dismiss a suggestion and search by name

## Trigger

An album with a barcode or store URL has a wrong suggestion on its page.

## Outcome

The album's page offers the name search, and its results are listed.
