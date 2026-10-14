---
appliesTo:
- type: entity
  id: album
  facts:
  - Release
- type: capability-scenario
  id: undo-matching-tagging
references:
- kind: doc
  role: intent
  target: docs/design/history.md
  title: Undoing a tagging
---

# An album's release ID changes on every file or none

Writing or undoing the release ID moves it on every file of the album, and the album's record follows; an undo that takes the album off its release returns it to Needs MBID with that release offered as a suggestion.
