---
appliesTo:
- type: entity
  id: bandcamp-purchase
  facts:
  - Private download
- type: capability
  id: check-release-group
references:
- kind: doc
  role: intent
  target: docs/design/contributions.md
  title: Possible mismatch
---

# A private download's URL is never offered to MusicBrainz

When Bandcamp marks a purchase private, its URL is never suggested as a link or sent to Harmony; its media can still be checked.
