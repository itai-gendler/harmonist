---
appliesTo:
- type: capability-scenario
  id: download-new-purchase
- type: capability-scenario
  id: download-without-exact-match
- type: capability-scenario
  id: look-up-barcode
- type: capability-scenario
  id: look-up-store-url
- type: capability-scenario
  id: reconcile-barcode-album
references:
- kind: code
  role: implementation
  target: src/harmonist/web/main.py#_apply_best_match
- kind: code
  role: implementation
  target: src/harmonist/match.py#match_releases
- kind: doc
  role: intent
  target: docs/design/matching.md
  title: Match confidence
---

# Only an exact, unique match is tagged without review

A release Harmonist finds by itself — from a download's store URL or a barcode — is written to the files unasked only when the files have its track count, every track is within four seconds of its length, and no other release fits them equally. Anything less becomes a suggested match, or a list of releases to choose from.

## Rationale

Barcodes are reused and one store page can be linked from several editions; choosing between equal fits would be taking whichever MusicBrainz listed first.
