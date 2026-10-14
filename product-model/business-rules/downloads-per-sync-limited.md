---
appliesTo:
- type: capability-scenario
  id: download-new-purchase
- type: entity
  id: settings
  facts:
  - Max downloads per sync
references:
- kind: code
  role: implementation
  target: src/harmonist/bandcamp_hook.py
- kind: doc
  role: intent
  target: docs/configuration.md
  title: '[bandcamp]'
---

# One sync downloads at most the set number of new purchases

Max downloads per sync (5 by default, 0 pauses downloads) caps the new purchases one sync downloads; the rest wait for the next sync. Purchases the owner approved and re-downloads do not count.
