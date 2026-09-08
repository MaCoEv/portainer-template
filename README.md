# Portainer Templates

Portainer [App Templates](https://docs.portainer.io/advanced/app-templates/build) for MaCoEv
apps. One repo, one `template.json`, one URL to add in Portainer under
**Settings → App Templates**:

```
https://raw.githubusercontent.com/MaCoEv/portainer-template/main/template.json
```

## Layout

Each app gets its own subfolder holding the stack file(s) `template.json` points to via
`repository.stackfile`; shared static assets (logos, ...) live in `assets/`.

- [`mdbdr-edge/`](mdbdr-edge/) — MongoDB Dump Scheduler Edge (`macoev/mdbdr`).

## Adding a new template

1. Add a subfolder with the `docker-compose.yml` (or other stack file) for the app.
2. Append an entry to the `templates` array in `template.json` pointing at it.
3. Push to `main` — Portainer re-fetches `template.json` on demand (no restart needed), so the
   new/updated template shows up next time someone opens App Templates.

Keep `template.json` and the stack files free of secrets and of application source — this repo
is intended to be reachable by Portainer without authentication.
