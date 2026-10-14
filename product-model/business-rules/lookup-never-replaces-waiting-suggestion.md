---
appliesTo:
- type: capability-scenario
  id: look-up-while-suggestion-waits
- type: entity
  id: suggested-match
  effect: creates
references:
- kind: code
  role: implementation
  target: src/harmonist/web/main.py#barcode_lookup
- kind: code
  role: implementation
  target: src/harmonist/web/main.py#manual_candidates
---

# A lookup never replaces a suggestion awaiting review

While a suggestion waits, a barcode or store URL lookup is answered without asking MusicBrainz and is checked again before anything is written; a suggestion changes only when the owner confirms or dismisses it.
