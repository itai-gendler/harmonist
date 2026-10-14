---
kind: edge
routes:
  web: Web
steps:
- text: The owner opens the Activity tab
  kind: actor
  actor: owner
  entities: []
  contexts:
    web:
      place: web::activity
- text: The history cannot be read
  kind: condition
  entities: []
  contexts:
    web:
      place: web::activity
- text: The Product says the feed cannot be read
  kind: product
  actor: owner
  entities: []
  contexts:
    web:
      place: web::activity
---

# The history cannot be read

## Trigger

Harmonist's history store cannot be read.

## Outcome

The feed says it cannot read the history rather than showing an empty feed.
