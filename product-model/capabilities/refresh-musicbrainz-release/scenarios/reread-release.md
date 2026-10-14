---
kind: primary
routes:
  web: Web
steps:
- text: The owner chooses to read the release from MusicBrainz again
  kind: actor
  actor: owner
  entities:
  - entity: release
    effect: reads
    facts:
    - Last read
  contexts:
    web:
      place: web::album
- text: The Product reads the release from MusicBrainz and keeps it
  kind: product
  actor: owner
  entities:
  - entity: release
    effect: changes
    facts:
    - Title
    - Artist credit
    - Tracklist
    - Barcode
    - Store links
    - Media
    - Last read
  contexts:
    web:
      place: web::album
- text: The Product redraws the album's tag and track comparison
  kind: product
  actor: owner
  entities:
  - entity: album
    effect: reads
    facts:
    - Tag values
  contexts:
    web:
      place: web::album
---

# Read the release again

## Trigger

The owner knows the release was edited on MusicBrainz.

## Outcome

The page compares the album with the release as MusicBrainz holds it now.
