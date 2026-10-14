---
references:
- kind: code
  role: implementation
  target: src/harmonist/gardener.py#refresh_flag
- kind: code
  role: implementation
  target: src/harmonist/formats/owned.py#Significance
- kind: doc
  role: intent
  target: docs/design/staying-current.md
  title: Staying current
---

# Tag update

The tag changes re-tagging an album would make now, against the release MusicBrainz holds and the owner's tagging settings: worked out by a dry run of the tagging itself, and written only when the owner applies it.

## Information kept

- **Significance** — how far the change reaches: Identity, Structure, Enrichment, Cosmetic or Settings
- **Changes** — each owned field's value now and after applying, and how many tracks it reaches
- **Release version** — the version of the MusicBrainz release it was found against
- **Follows settings** — the change only brings the album into line with a tagging setting rather than with anything MusicBrainz did
- **Tracklist changed** — tracks were added, removed or renumbered, so the pairing of files with tracks must be reviewed first

## States

### Available

Listed under the Library's Tag updates filter and on the album's page.

### Ignored

Taken off the list until MusicBrainz next changes the release.

### Applied

Written to the album's files.
