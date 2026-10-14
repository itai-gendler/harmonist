---
singleton: true
references:
- kind: code
  role: implementation
  target: src/harmonist/config.py
- kind: doc
  role: intent
  target: docs/configuration.md
  title: Configuration
---

# Settings

The owner's settings, kept once for the whole library and applied straight away.

## Information kept

- **Create cover.jpg in album folders** — Never, or Only when missing, for whether a missing folder cover is suggested
- **Album title** — Title only, Title + release disambiguation, or Title + release disambiguation if needed
- **Standardize artist names** — write each artist as credited on the release, as their own name unless the credit is a former name, or always as their own name
- **Always standardize multi-valued artist tags** — the artist lists players group by carry each artist's own name
- **Library updates** — Off, or Find updates for review in the background
- **Download format** — the format Bandcamp purchases are downloaded in
- **Max downloads per sync** — how many new purchases one sync downloads; 0 pauses downloads
- **MusicBrainz user agent** — how Harmonist identifies the owner to MusicBrainz
- **Log level** — debug, info, warning or error
- **Bandcamp login cookies** — the owner's Bandcamp login, as a cookies.txt file
