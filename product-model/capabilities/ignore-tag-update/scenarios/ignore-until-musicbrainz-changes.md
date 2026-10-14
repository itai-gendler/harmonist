---
kind: primary
routes:
  web: Web
steps:
- text: The owner ticks Ignore until MusicBrainz changes on the album's page
  kind: actor
  actor: owner
  entities:
  - entity: tag-update
    effect: reads
    facts:
    - Significance
    - Changes
  - entity: album
    effect: reads
    facts: []
  contexts:
    web:
      place: web::album
- text: The Product records the ignore against the release version the update was found on
  kind: product
  actor: owner
  entities:
  - entity: tag-update
    effect: changes
    from: Available
    to: Ignored
    facts:
    - Release version
  contexts:
    web:
      place: web::album
---

# Ignore an update until MusicBrainz changes

## Trigger

An update from MusicBrainz looks wrong and the owner has asked for it to be corrected there.

## Outcome

The album leaves the Tag updates list; nothing is written.
