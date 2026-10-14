---
appliesTo:
- type: entity
  id: suggested-match
- type: capability
  id: confirm-suggestion
- type: capability
  id: dismiss-suggestion
references:
- kind: code
  role: implementation
  target: src/harmonist/models.py#MatchCandidate
- kind: doc
  role: intent
  target: docs/design/history.md
  title: Two records, one store
---

# A suggested match changes no file until the owner confirms it

Finding, listing or dismissing a suggestion writes nothing to the album's files; confirming it is the decision the album's History records, with the release and how it was found.
