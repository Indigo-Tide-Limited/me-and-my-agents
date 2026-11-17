Announce a running preview server to the coder-team UI.

After starting a dev server, run:

```bash
ct-preview <port> "<label>"
```

Arguments:
- `port` — the port number your server is listening on (use `ct-port-alloc` to get one first)
- `label` — a human-readable description shown in the UI (e.g. "Frontend dev server")

This makes the preview accessible from the coder-team dashboard.
