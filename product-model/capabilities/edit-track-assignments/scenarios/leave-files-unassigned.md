---
kind: alternative
routes:
  web: Web
steps:
- text: The owner leaves a file opposite a gap and chooses Accept changes
  kind: actor
  actor: owner
  entities:
  - entity: album
    effect: reads
    facts:
    - Tracks on disk
  contexts:
    web:
      place: web::album
- text: The Product writes only the release ID to the unassigned file and the track tags to the others
  kind: product
  actor: owner
  entities:
  - entity: album
    effect: changes
    facts:
    - Tag values
  - entity: tagging
    effect: creates
    facts:
    - Release
    - Field changes
    - Files
    - Written at
  contexts:
    web:
      place: web::album
---

# Leave some files unassigned

## Trigger

Some files belong to the release but match none of its tracks.

## Outcome

The unassigned files get only the album's release ID and keep their other tags.

## Edge cases

- A file that already carries a track ID cannot be left unassigned.
