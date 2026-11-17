Allocate the next free port from your assigned preview port range.

Run this command:

```bash
ct-port-alloc
```

It outputs a single port number on stdout. Use this port when starting any dev server or preview. The port range is managed by coder-team to avoid collisions between agents.
