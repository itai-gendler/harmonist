---
kind: validation
routes:
  web: Web
steps:
- text: The owner saves the Bandcamp setup with nothing pasted or chosen
  kind: actor
  actor: owner
  entities: []
  contexts:
    web:
      place: web::bandcamp-sync-setup
- text: The Product asks for the cookies.txt contents or a file
  kind: product
  actor: owner
  entities: []
  contexts:
    web:
      place: web::bandcamp-sync-setup
---

# Save without cookies

## Trigger

The owner saves with nothing pasted and no file chosen.

## Outcome

The owner is asked for the cookies and nothing is kept.
