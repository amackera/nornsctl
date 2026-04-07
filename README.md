# nornsctl

CLI for the [Norns](https://github.com/amackera/norns) durable agent runtime.

Thin wrapper over the Norns REST API. Inspect runs, tail events, retry failed runs, check worker status.

## Status

Not yet implemented. This README is the plan.

## Planned commands

```
nornsctl agents list                     List agents
nornsctl agents show <id|name>           Show agent details

nornsctl runs list [--agent <name>]      List runs (optionally filtered by agent)
nornsctl runs show <id>                  Show run details + failure inspector
nornsctl runs events <id>                Print event log
nornsctl runs retry <id>                 Retry a failed run with the same input
nornsctl runs tail <id>                  Stream events in real-time (WebSocket)

nornsctl workers list                    List connected workers
nornsctl workers status                  Worker health summary
```

## Configuration

```bash
export NORNS_URL=http://localhost:4000
export NORNS_API_KEY=nrn_...
```

Or via flags: `nornsctl --url http://... --token nrn_... runs list`

## Implementation

- Python (single dependency: `httpx`)
- Packaged via `uv` / PyPI as `nornsctl`
- Uses the same REST API as `norns-sdk-python` client, but optimized for terminal output
- Real-time event tailing via WebSocket

## License

MIT
