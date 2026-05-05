# protopep-status

Remote status JSON read by the [ProtoPep](https://github.com/aanthonyle28/PostOpPep) iOS app on launch. Powers the dead-screen gate (maintenance mode + force-update).

**Live URL:** https://aanthonyle28.github.io/protopep-status/status.json

## Schema

```json
{
  "status": "ok" | "maintenance" | "force_update",
  "minVersion": "1.0.0",
  "message": "string shown on the dead screen",
  "learnMoreURL": "https://..."
}
```

- `status` and `minVersion` required; rest optional.
- `learnMoreURL` must be `http`/`https` — the app rejects other schemes at decode.
- App fails open on any decode/network error.

## Editing

Edit `docs/status.json` on master. GitHub Pages serves from `/docs`. Changes propagate in ~1 minute.

To put the app in maintenance:
```json
{ "status": "maintenance", "minVersion": "1.0.0", "message": "Back in about an hour." }
```

To force an update:
```json
{ "status": "force_update", "minVersion": "1.2.0", "message": "Update on the App Store." }
```

Revert to `"status": "ok"` to re-open.
