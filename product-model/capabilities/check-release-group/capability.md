---
availability:
- place: web
references:
- kind: code
  role: implementation
  target: src/harmonist/web/main.py#contribution_editions
- kind: code
  role: implementation
  target: src/harmonist/contributions.py#sibling_check
- kind: doc
  role: intent
  target: docs/design/contributions.md
  title: Contributions and possible mismatches
---

# Check the release group

For an album whose files are a download or a CD rip, Harmonist compares the album's source evidence — its store URL, the files' original barcode and their media — with every release in its release group, to find a possible mismatch or, once the match is settled, what its release is missing on MusicBrainz.
