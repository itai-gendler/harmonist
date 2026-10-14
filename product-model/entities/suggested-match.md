---
references:
- kind: code
  role: implementation
  target: src/harmonist/models.py#MatchCandidate
- kind: code
  role: implementation
  target: src/harmonist/match.py#assess_match
- kind: doc
  role: intent
  target: docs/design/matching.md
  title: Matching
---

# Suggested match

A MusicBrainz release Harmonist proposes for an album but has not written: found by evidence that does not settle the match on its own, so the owner reviews it side by side and confirms or dismisses it.

## Information kept

- **Release** — the MusicBrainz release suggested
- **How it was found** — by store URL, barcode, name search, a pasted MusicBrainz ID, or an undone tagging
- **Confidence** — Exact when the track count matches and every track is within four seconds of the release's length for it, otherwise Approximate
- **Track comparison** — the files beside the release's tracks, with their length differences
- **No purchase found** — a full Bandcamp sync found no purchase for the album, so its own release is kept here read-only
- **Owned purchase** — for a possibly mis-tagged album, the Bandcamp purchase of another release in the same release group that the files may really be

## States

### Proposed

Waiting for the owner's review; nothing has been written.

### Confirmed

The owner confirmed it and the album is now matched to its release.

### Dismissed

The owner dismissed it; the album stays in Needs MBID for another search.
