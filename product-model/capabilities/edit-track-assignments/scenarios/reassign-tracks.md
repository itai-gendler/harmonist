---
kind: primary
routes:
  web: Web
steps:
- text: The owner chooses Edit track assignments on the album's page
  kind: actor
  actor: owner
  entities:
  - entity: album
    effect: reads
    facts:
    - Tracks on disk
    - Release
  - entity: release
    effect: reads
    facts:
    - Tracklist
  contexts:
    web:
      place: web::album
- text: The Product shows each file beside the track it is paired with and marks the pairings it guessed
  kind: product
  actor: owner
  entities: []
  contexts:
    web:
      place: web::album
- text: The owner moves files and tracks until each file sits beside its own track, and chooses Accept changes
  kind: actor
  actor: owner
  entities: []
  contexts:
    web:
      place: web::album
- text: The Product checks the files and release are as the editor showed them and writes each file's track tags
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

# Correct which file is which track

## Trigger

Files of a matched album are paired with the wrong tracks.

## Outcome

Each file carries the tags of the track the owner paired it with, including its release-track ID, and the tagging is recorded.

## Edge cases

- Reset returns to the automatic pairing; Cancel returns to the last accepted pairing.
- Durations never decide a pairing.
