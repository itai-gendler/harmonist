---
kind: alternative
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
    - Release
  contexts:
    web:
      place: web::album
- text: The Product compares the release with the album's evidence across the whole group
  kind: product
  actor: owner
  entities:
  - entity: release
    effect: reads
    facts:
    - Store links
    - Barcode
  - entity: album
    effect: reads
    facts: []
  contexts:
    web:
      place: web::album
- text: No other release in the group links the store URL, or the release has no barcode
  kind: condition
  entities: []
  contexts:
    web:
      place: web::album
- text: The Product shows the first thing the release is missing, ready to copy into MusicBrainz's editor
  kind: product
  actor: owner
  entities:
  - entity: album
    effect: changes
    facts:
    - MB contribution
  contexts:
    web:
      place: web::album
---

# Find what MusicBrainz is missing

## Trigger

The album's match is settled and its release lacks the files' store link or barcode.

## Outcome

One finding is shown at a time, with a link to the release's editor on MusicBrainz and the value ready to copy.

## Edge cases

- A barcode that disagrees with MusicBrainz's is shown as something to look into, not a replacement.
- A CD rip's barcode is never offered.
