---
relations:
- entity: album
  verb: supplies
  cardinality: one-to-one
references:
- kind: code
  role: implementation
  target: src/harmonist/bandcamp_hook.py#HarmonistSyncer
- kind: code
  role: implementation
  target: src/harmonist/pending_downloads.py#PendingPurchase
- kind: doc
  role: intent
  target: docs/design/bandcamp.md
  title: Bandcamp
---

# Bandcamp purchase

An album in the owner's Bandcamp collection, as a sync sees it: something to link to an album already on disk, download, or set aside.

## Information kept

- **Artist** — the artist Bandcamp names
- **Title** — the title Bandcamp names
- **Purchase URL** — the Bandcamp page it was bought from
- **Private download** — Bandcamp marks it private, so its URL is never offered as a link or sent to Harmony

## States

### To consider

The next sync will consider it.

### Potential download

A sync could not confidently tie it to an album on disk, so it waits in the Inbox for the owner's decision.

### Approved

The owner asked for it to be downloaded on the next sync, past link-only mode and the per-sync limit.

### Won't download

Set aside by the owner and listed under Won't download in Settings.

### In library

Downloaded or linked to an album on disk, so no later sync downloads it.
