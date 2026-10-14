---
kind: alternative
routes:
  web: Web
steps:
- text: The owner chooses Undo tag changes on the tagging that matched the album
  kind: actor
  actor: owner
  entities:
  - entity: tagging
    effect: reads
    facts:
    - Release
  - entity: album
    effect: reads
    facts: []
  contexts:
    web:
      place: web::album
- text: The Product takes the release ID off every file, or none, and puts the earlier values back
  kind: product
  actor: owner
  entities:
  - entity: album
    effect: changes
    from: Complete
    to: Needs MBID
    facts:
    - Release
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
- text: The Product offers the release again as a suggestion
  kind: product
  actor: owner
  entities:
  - entity: suggested-match
    effect: creates
    to: Proposed
    facts:
    - Release
    - How it was found
  contexts:
    web:
      place: web::album
---

# Undo the tagging that matched the album

## Trigger

The tagging being undone is the one that first matched the album.

## Outcome

The release ID comes off every file, and the album returns to Needs MBID with that release suggested.
