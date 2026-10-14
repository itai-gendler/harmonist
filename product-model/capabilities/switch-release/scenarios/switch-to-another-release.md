---
kind: primary
routes:
  web: Web
steps:
- text: The owner chooses Use beside another release in the group
  kind: actor
  actor: owner
  entities:
  - entity: album
    effect: reads
    facts:
    - Possible mismatch
  - entity: release
    effect: reads
    facts:
    - Title
    - Media
  contexts:
    web:
      place: web::album
- text: The Product shows the files beside that release's tracks with the tag changes and artwork switching would write
  kind: product
  actor: owner
  entities:
  - entity: release
    effect: reads
    facts:
    - Tracklist
    - Cover art
  contexts:
    web:
      place: web::album
- text: The owner confirms the switch
  kind: actor
  actor: owner
  entities: []
  contexts:
    web:
      place: web::album
- text: The Product writes the chosen release's tags and reviewed artwork into every folder of the album and records it as the release bought
  kind: product
  actor: owner
  entities:
  - entity: album
    effect: changes
    facts:
    - Release
    - Tag values
    - Track and disc totals
    - Accepted release
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

# Switch an album to another release in its group

## Trigger

The release group check shows the album is probably another release.

## Outcome

The album is tagged as the chosen release, recorded as the one bought, and the tagging is in its History.

## Edge cases

- A CD rip can only switch to a physical release, and a download to a digital one.
