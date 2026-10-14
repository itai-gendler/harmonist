---
appliesTo:
- type: entity
  id: album
  facts:
  - Tag values
- type: capability
  id: apply-tag-updates
- type: capability
  id: confirm-suggestion
references:
- kind: code
  role: implementation
  target: src/harmonist/formats/owned.py
- kind: doc
  role: intent
  target: docs/design/tagging.md
  title: The owned set
---

# Harmonist writes only the tags it owns

Every tagging clears and writes exactly the owned set of tags, under Picard's names, in every format. Everything else on a file — the comment carrying a store URL, genres, ReplayGain, ratings, other tools' credits — is left exactly as found, and the original UPC a download was sold under survives tagging and undo.

## Rationale

A field the new release lacks must be removed rather than left over from the previous release, while tags Harmonist does not understand belong to the owner and other tools.
