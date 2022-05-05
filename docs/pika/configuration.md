# Configuration

Pika uses TOML for configuration. You can either supply the configuration as a
file or as an environment variable.

## Sources

### File

File configuration is easier when running the binary directly. Pika will check
a few known locations for a config file, or if `--config` is specified as an
argument when running Pika, it will use that path.

You can also set the environment variable `PIKA_CONFIG_FILE` to a config file path.

#### Known config file locations

These known locations are checked in this order.

* `$(BINARY_DIR)/pika.toml`
* `~/.config/pika.toml`
* `/etc/pika/pika.toml`

### Environment variable

When running Pika in Docker, set the `PIKA_CONFIG` environment variable to the
contents of your configuration file and Pika will apply it when it loads. You
can of course also use a volume mount and set the `PIKA_CONFIG_FILE` to use a specific file.

```yaml
version: '3'

services:
  pika:
    image: ghcr.io/picotorrent/pika:latest
    environment:
      PIKA_CONFIG: |
        [http]
        host = "localhost"
        port = 1337
    ports:
        - "1337:1337"
```

## Reference

This is a reference configuration file that tries to show and explain all
possible settings and their values.

```toml
# Pika reference config.

# The http section sets options for the HTTP server.
[http]
host = "127.0.0.1" # Which interface should the server bind to.
port = 1337        # Which port should the server listen on.

# A plugin loaded from a file.
[[plugins]]
file = "/etc/pika/plugin1.js"

# An inline plugin.
[[plugins]]
script = """
export default function torrentAdded({ torrent }) {
    torrent.pause();
}
"""
```
