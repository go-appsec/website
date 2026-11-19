---
title: CLI overview
description: Sectool CLI command families and their relationship to the MCP server.
---

The CLI provides human-oriented access to the server's testing state, with tables, filters, and local export bundles. Proxy, replay, crawl, OAST, diff, reflection, JavaScript analysis, and notes commands connect to a running MCP server.

| Command family | Purpose |
| --- | --- |
| `sectool mcp` | Run the server |
| `sectool proxy` | Summarize, list, inspect, export, or clear history; inspect cookies and manage rules |
| `sectool replay` | Send requests, inspect replay flows, or create editable bundles |
| `sectool crawl` | Create and inspect crawl sessions and discovered forms |
| `sectool oast` | Create sessions and inspect callback events |
| `sectool diff` | Compare two flows with a required scope |
| `sectool reflected` | Find request values reflected in a response |
| `sectool js` | Analyze a captured JS/HTML response or expand an endpoint |
| `sectool notes` | List, inspect, or delete saved notes and findings; requires `--notes` on the server |
| `sectool encode` / `decode` | Local URL, Base64, and HTML transformations |
| `sectool hash` | Local digest and HMAC computation |
| `sectool jwt` | Local JWT decoding and inspection |
| `sectool version` | Show the installed version |

JWT decoding is inspection, not cryptographic signature verification.

## Get exact options

```bash
sectool --help
sectool proxy --help
sectool replay send --help
sectool crawl create --help
sectool oast --help
sectool notes --help
```

This page is an overview rather than an exhaustive flag reference. The installed executable's help is the reference for its version. Guides use current source-verified options and explicitly mark returned IDs as placeholders.

## Review saved notes

Start the server with notes enabled, for example:

```bash
sectool mcp --proxy-port 8080 --workflow explore --notes
```

In another terminal, list notes saved by an agent or sidecar:

```bash
sectool notes list
sectool notes list --type finding --limit 20
sectool notes list --flow-id FLOW_ID --contains "header"
sectool notes get NOTE_ID
```

Replace `FLOW_ID` with a captured flow ID and `NOTE_ID` with an ID returned by `notes list`. `--flow-id` also accepts a comma-separated list; `--contains` searches content case-insensitively. List output abbreviates content; `notes get` shows the full note.

To remove a saved note, run `sectool notes delete NOTE_ID`. Creating and updating notes uses the MCP `notes_save` tool. Notes remain experimental; a `finding` label does not establish a confirmed vulnerability.

## Common tasks

- [Inspect captured traffic](../../guides/traffic/)
- [Replay and compare responses](../../guides/replay/)
- [Analyze JavaScript and crawl](../../guides/discovery/)
- [Observe out-of-band events](../../guides/oast/)
