---
appliesTo:
- type: entity
  id: album
  effect: changes
  to: Incomplete
- type: capability-scenario
  id: confirm-with-tracks-missing
- type: capability-scenario
  id: apply-update-short-of-tracks
references:
- kind: code
  role: implementation
  target: src/harmonist/tagger.py#TagMismatchError
- kind: doc
  role: intent
  target: docs/design/matching.md
  title: When the counts differ
---

# A release's tags go onto fewer files than it has tracks only with the owner's consent

A tagging refuses to write a release's tags onto fewer files than the release has tracks unless the owner confirms the album with tracks missing or chooses Re-tag as incomplete; then the files get the release's own totals and the album is listed as Incomplete. More files than tracks is possible only through a track assignment review.

## Rationale

It is how a half-finished download would otherwise be tagged as the whole album.
