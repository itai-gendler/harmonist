---
kind: primary
routes:
  web: Web
steps:
- text: The owner expands the album's History and reads what a tagging changed
  kind: actor
  actor: owner
  entities:
  - entity: tagging
    effect: reads
    facts:
    - Field changes
    - Written at
  - entity: album
    effect: reads
    facts: []
  contexts:
    web:
      place: web::album
- text: The owner chooses Undo tag changes on that tagging
  kind: actor
  actor: owner
  entities:
  - entity: tagging
    effect: reads
    facts: []
  contexts:
    web:
      place: web::album
- text: The Product reads every file of the album first, finding renamed files by release-track ID, recording ID and position
  kind: product
  actor: owner
  entities:
  - entity: tagging
    effect: reads
    facts:
    - Files
  - entity: album
    effect: reads
    facts: []
  contexts:
    web:
      place: web::album
- text: The Product puts back each field that still carries what the tagging wrote and records the undo
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

# Undo a tagging

## Trigger

A tagging changed tags the owner wants back.

## Outcome

The fields that tagging wrote carry their earlier values again, and the undo is itself in the History.

## Edge cases

- An undo with nothing left to change records nothing.
- The undo can itself be undone.
