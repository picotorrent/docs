---
sidebar_position: 3
---

# `session.addTorrent`

Adds a torrent to the BitTorrent session.

## Request

```json
{
  "id": 1,
  "jsonrpc": "2.0",
  "method": "session.addTorrent",
  "params": {
    "save_path": "/tmp",
    "ti": "<base64 encoded buffer of torrent file>"
  }
}
```

## Response

```json
{
  "id": 1,
  "jsonrpc": "2.0",
  "result": {
    "info_hash": "20-byte info-hash"
  }
}
```

### Errors


