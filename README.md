# Piphi Network Openepaperlink

Generated PiPhi integration runtime.

## Run locally

```bash
pdm install -G dev
pdm run uvicorn piphi_network_openepaperlink.main:app --reload --port 4219
pdm run pytest
pdm run python scripts/validate.py
```

The runtime listens on port `4219` by default and exposes the common PiPhi runtime route contract:

- `GET /health`
- `GET /diagnostics`
- `POST /discover`
- `POST /config`
- `POST /config/sync`
- `POST /deconfigure`
- `POST /deconfigure/{config_id}`
- `GET /state`
- `GET /contract`
- `GET /entities`
- `GET /events`
- `POST /events/device/{config_id}/example`
- `POST /telemetry/example`
- `POST /telemetry/device/{config_id}/example`
- `POST /command`

## Capability coverage

`capability-catalog.json` inventories OpenEPaperLink access-point health,
per-tag radio and battery state, display transfers, rendering, optional LEDs,
buzzers, NFC and GPIO, scheduling, maintenance, and safety boundaries. Each
candidate is classified as implemented, planned, or excluded, and contract
tests prevent unimplemented features from being advertised.

Tag features remain planned until AP transport, firmware and tag-type
negotiation, rendering fixtures, bounded transfer queues, and representative
hardware tests exist. The starter runtime currently exposes only connectivity
and refresh.

## Manifest

`manifest.json` is a starter manifest. Before publishing, update:

- `image`
- `version`
- capabilities and commands
- config fields and identity fields
- entity metadata

## Docker

```bash
docker build -t docker.io/piphinetwork/piphi-network-openepaperlink:0.1.0 .
docker run --rm -p 4219:4219 docker.io/piphinetwork/piphi-network-openepaperlink:0.1.0
```
