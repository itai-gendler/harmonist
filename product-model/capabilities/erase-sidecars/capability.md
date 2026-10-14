---
domain: settings
availability:
- place: web
references:
- kind: code
  role: implementation
  target: src/harmonist/web/main.py#erase_sidecars
- kind: code
  role: implementation
  target: src/harmonist/sidecar.py#delete_all
- kind: doc
  role: intent
  target: docs/troubleshooting.md
  title: Remove Harmonist completely
---

# Erase sidecars

From Settings → Maintenance the owner removes Harmonist's record from every album folder; audio and tags stay, and albums are worked out again from their tags.
