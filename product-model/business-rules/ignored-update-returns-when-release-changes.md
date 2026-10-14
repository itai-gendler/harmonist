---
appliesTo:
- type: capability-scenario
  id: ignored-update-returns
- type: capability
  id: ignore-tag-update
references:
- kind: code
  role: implementation
  target: src/harmonist/gardener.py#is_ignored
- kind: doc
  role: intent
  target: docs/how-it-works.md
  title: Keeping tags up to date
---

# An ignored update returns when MusicBrainz next changes the release

Ignoring is recorded against the version of the release the update was found on; the first different version lists the album's update again, which is usually when the owner's edit on MusicBrainz is accepted.
