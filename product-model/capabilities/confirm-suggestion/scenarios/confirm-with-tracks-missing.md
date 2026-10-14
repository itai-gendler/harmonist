---
kind: alternative
routes:
  web: Web
steps:
- text: The owner reviews a suggestion whose release has tracks the files do not
  kind: actor
  actor: owner
  entities:
  - entity: suggested-match
    effect: reads
    facts:
    - Track comparison
  contexts:
    web:
      place: web::inbox
- text: The owner chooses Confirm suggestion
  kind: actor
  actor: owner
  entities:
  - entity: suggested-match
    effect: reads
    facts:
    - Release
  contexts:
    web:
      place: web::inbox
- text: The Product writes the release's tags and totals into the files present and records the tagging
  kind: product
  actor: owner
  entities:
  - entity: album
    effect: changes
    from: Needs MBID
    to: Incomplete
    facts:
    - Release
    - Tag values
    - Track and disc totals
  - entity: suggested-match
    effect: changes
    from: Proposed
    to: Confirmed
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
      place: web::inbox
---

# Confirm a release with tracks missing

## Trigger

The suggested release lists more tracks than the album has on disk.

## Outcome

The files the owner has get the release's tags and totals, and the album is listed as Incomplete.
