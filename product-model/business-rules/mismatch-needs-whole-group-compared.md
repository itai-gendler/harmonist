---
appliesTo:
- type: capability
  id: check-release-group
- type: entity
  id: album
  facts:
  - Possible mismatch
references:
- kind: code
  role: implementation
  target: src/harmonist/contributions.py#sibling_check
- kind: doc
  role: intent
  target: docs/design/contributions.md
  title: Possible mismatch
---

# A possible mismatch is flagged only after the whole release group is compared

A group with more than 100 releases, a release whose media MusicBrainz has not specified, or a failed request makes no finding at all; and each reason must be something the files have that the matched release lacks.
