---
kind: alternative
routes:
  web: Web
steps:
- text: The owner ticks or unticks Link-only beside Sync Bandcamp and syncs
  kind: actor
  actor: owner
  entities: []
  contexts:
    web:
      place: web::inbox
- text: The Product runs this sync in the chosen mode, paging the whole collection when it is link-only
  kind: product
  actor: owner
  entities: []
  contexts:
    web:
      place: web::inbox
---

# Choose link-only for one sync

## Trigger

The owner changes the Link-only box under the Sync Bandcamp button before syncing.

## Outcome

That one sync runs in the mode the owner chose; the next sync decides again for itself.

## Decision points

### Which mode runs?

Does the owner's choice differ from what the waiting albums call for?

- Link-only ticked with nothing waiting → the sync links purchases to albums on disk and downloads nothing.
- Link-only unticked while albums wait under Needs Linking → the sync also downloads new purchases.
