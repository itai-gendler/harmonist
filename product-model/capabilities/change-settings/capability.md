---
domain: settings
availability:
- place: web
references:
- kind: code
  role: implementation
  target: src/harmonist/web/main.py#settings_save
- kind: code
  role: implementation
  target: src/harmonist/config.py#TaggingConfig
- kind: code
  role: implementation
  target: src/harmonist/gardener.py#recheck_for_settings
- kind: doc
  role: intent
  target: docs/configuration.md
  title: Configuration
---

# Change settings

The owner changes the settings on the Settings page — Tagging, Background Updates, Bandcamp and Server — and saves them together; they apply straight away.
