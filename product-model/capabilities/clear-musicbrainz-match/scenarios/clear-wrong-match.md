---
kind: primary
routes:
  web: Web
steps:
- text: The owner chooses Wrong MusicBrainz match on the album's page
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
- text: The Product clears the album's release without suggesting it again, keeping its store URL and purchase
  kind: product
  actor: owner
  entities:
  - entity: album
    effect: changes
    from: Complete
    to: Needs MBID
    facts:
    - Release
  contexts:
    web:
      place: web::album
---

# Clear a wrong match

## Trigger

The owner believes a matched album has the wrong release.

## Outcome

The album waits in Needs MBID with the search tools, its files untouched.
