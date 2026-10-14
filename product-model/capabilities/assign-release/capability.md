---
availability:
- place: web
references:
- kind: code
  role: implementation
  target: src/harmonist/web/main.py#manual_assign
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

# Assign a release

The owner names the release for an unmatched album — by pasting a MusicBrainz release URL or ID and choosing Assign & Tag, or by choosing Use on a listed release. When the files fit the release exactly the album is tagged at once; otherwise the release becomes a suggestion to review.
