---
kind: primary
routes:
  web: Web
steps:
- text: The owner chooses Set up Bandcamp sync
  kind: actor
  actor: owner
  entities: []
  contexts:
    web:
      place: web::bandcamp-sync-setup
- text: The owner pastes or uploads their cookies.txt file and saves it
  kind: actor
  actor: owner
  entities:
  - entity: settings
    effect: changes
    facts:
    - Bandcamp login cookies
  contexts:
    web:
      place: web::bandcamp-sync-setup
- text: The Product reloads the page with Sync Bandcamp in the header
  kind: product
  actor: owner
  entities: []
  contexts:
    web:
      place: web::inbox
---

# Give Harmonist the Bandcamp login cookies

## Trigger

The owner wants Harmonist to sync their Bandcamp purchases.

## Outcome

The cookies are kept and the header offers Sync Bandcamp.
