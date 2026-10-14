---
kind: primary
routes:
  web: Web
steps:
- text: The owner opens the Library
  kind: actor
  actor: owner
  entities:
  - entity: album
    effect: reads
    facts:
    - Title
    - Artist
    - Added
  contexts:
    web:
      place: web::library
- text: The Product shows the albums newest first with a count for every filter
  kind: product
  actor: owner
  entities:
  - entity: album
    effect: reads
    facts:
    - Origin
    - Track and disc totals
    - Accepted as complete
    - Possible mismatch
    - MB contribution
  - entity: tag-update
    effect: reads
    facts:
    - Significance
  - entity: artwork-update
    effect: reads
    facts:
    - Kind
  contexts:
    web:
      place: web::library
- text: The owner chooses filters such as Origin, Incomplete, Format, Tag updates or Artwork updates, and searches by artist
  kind: actor
  actor: owner
  entities:
  - entity: album
    effect: reads
    facts:
    - Origin
    - Tracks on disk
  - entity: tag-update
    effect: reads
    facts:
    - Significance
  - entity: artwork-update
    effect: reads
    facts:
    - Kind
  contexts:
    web:
      place: web::library
- text: The Product shows only the albums matching every filter and the search
  kind: product
  actor: owner
  entities:
  - entity: album
    effect: reads
    facts:
    - Title
    - Artist
  contexts:
    web:
      place: web::library
---

# Find albums that could be better

## Trigger

The owner wants to see which albums have something to improve.

## Outcome

Only albums matching every chosen filter and the search are shown, and the view can be returned to by its address.

## Edge cases

- New shows albums added within the last seven days.
- Incomplete leaves out albums the owner accepted as complete.
- Counts describe albums, not individual images or tag fields.
- The page size is remembered; a filter or search is not.
