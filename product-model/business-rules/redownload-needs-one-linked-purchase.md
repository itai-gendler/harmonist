---
appliesTo:
- type: entity
  id: album
  effect: removes
permits:
- actors:
  - owner
  when:
  - fact: Linked purchase
    present: true
references:
- kind: code
  role: implementation
  target: src/harmonist/web/main.py#redownload
---

# Re-download is offered only for an album linked to a single Bandcamp purchase

An album linked only to several candidate purchases cannot be re-downloaded, since fetching one of them would be a guess.
