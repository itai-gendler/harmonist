---
entities:
- entity: settings
  shows:
  - Create cover.jpg in album folders
  - Album title
  - Standardize artist names
  - Always standardize multi-valued artist tags
  - Library updates
  - Download format
  - Max downloads per sync
  - MusicBrainz user agent
  - Log level
  - Bandcamp login cookies
  collects:
  - Create cover.jpg in album folders
  - Album title
  - Standardize artist names
  - Always standardize multi-valued artist tags
  - Library updates
  - Download format
  - Max downloads per sync
  - MusicBrainz user agent
  - Log level
- entity: bandcamp-purchase
  shows:
  - Artist
  - Title
entryPoints:
- web: /settings
references:
- kind: code
  role: implementation
  target: templates/settings.html
- kind: code
  role: implementation
  target: src/harmonist/web/main.py#settings_page
- kind: doc
  role: intent
  target: docs/configuration.md
  title: Configuration
---

# Settings

The owner's settings in sections — Tagging, Background Updates, Bandcamp and
Server — saved together, with the Bandcamp purchases set aside as Won't
download, how full the artwork backups and cache are, and the Maintenance
control that erases Harmonist's album records.
