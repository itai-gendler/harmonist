---
domain: inbox
availability:
- place: web
references:
- kind: code
  role: implementation
  target: src/harmonist/web/main.py#pending_download
- kind: code
  role: implementation
  target: src/harmonist/pending_downloads.py#approve
---

# Download a potential download

The owner asks for a purchase the sync set aside to be downloaded; the next sync fetches it even while it runs link-only and beyond the per-sync limit.
