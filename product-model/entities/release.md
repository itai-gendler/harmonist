---
relations:
- entity: album
  verb: matches
  cardinality: one-to-many
references:
- kind: code
  role: implementation
  target: src/harmonist/mb_cache.py
- kind: code
  role: implementation
  target: src/harmonist/caa_cache.py
- kind: doc
  role: intent
  target: docs/design/external-services.md
  title: External services
---

# MusicBrainz release

One edition of an album on MusicBrainz, as Harmonist last read it: the source of every tag it writes, kept so album pages and checks can be answered without asking again.

## Information kept

- **Title** — the release title and its disambiguation
- **Artist credit** — the artists credited, with each artist's own name and aliases
- **Tracklist** — the media and tracks, with track lengths and identifiers
- **Barcode** — the release's barcode
- **Store links** — the store pages MusicBrainz links to the release
- **Release group** — the group gathering every release of the same album
- **Media** — the formats of its media, physical or digital
- **Cover art** — the images the Cover Art Archive lists for the release
- **Last read** — when Harmonist last read it from MusicBrainz
- **Cover Art Archive checked** — when Harmonist last asked the Cover Art Archive about it
