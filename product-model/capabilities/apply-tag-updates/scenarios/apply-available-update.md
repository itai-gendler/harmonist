---
kind: primary
routes:
  web: Web
steps:
- text: The owner reads the update's changes and how far each reaches on the album's page
  kind: actor
  actor: owner
  entities:
  - entity: tag-update
    effect: reads
    facts:
    - Significance
    - Changes
    - Follows settings
  - entity: album
    effect: reads
    facts: []
  contexts:
    web:
      place: web::album
- text: The owner chooses Apply updates
  kind: actor
  actor: owner
  entities: []
  contexts:
    web:
      place: web::album
- text: The Product reads the release fresh from MusicBrainz and writes the changed owned tags, and any included artwork additions, into every folder of the album
  kind: product
  actor: owner
  entities:
  - entity: release
    effect: reads
    facts:
    - Tracklist
  - entity: album
    effect: changes
    facts:
    - Tag values
    - Track and disc totals
    - Embedded artwork
  - entity: tag-update
    effect: changes
    from: Available
    to: Applied
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
      place: web::album
---

# Apply an album's tag update

## Trigger

An album has a tag update waiting.

## Outcome

The album's files carry what MusicBrainz says now, the tagging is in its History, and the update is gone.

## Edge cases

- A file with nothing to change is not written, so its modification time is kept.
- Artwork that cannot be read never stops the tags being written.
