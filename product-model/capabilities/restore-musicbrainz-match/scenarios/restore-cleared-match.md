---
kind: primary
routes:
  web: Web
steps:
- text: The owner chooses Undo beside the cleared match in the album's History
  kind: actor
  actor: owner
  entities:
  - entity: album
    effect: reads
    facts:
    - Tracks on disk
  contexts:
    web:
      place: web::album
- text: The Product links the album back to the release its files carry and drops any waiting suggestion
  kind: product
  actor: owner
  entities:
  - entity: album
    effect: changes
    from: Needs MBID
    to: Complete
    facts:
    - Release
  - entity: suggested-match
    effect: removes
    from: Proposed
  contexts:
    web:
      place: web::album
---

# Undo clearing a match

## Trigger

The owner cleared an album's match and every file still names that release.

## Outcome

The album is matched to that release again and any suggestion made since is gone.
