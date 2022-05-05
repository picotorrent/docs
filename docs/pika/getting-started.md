---
sidebar_position: 2
---

# Getting started

Pika is only officially released as Docker images, so to run it you need Docker
installed. This makes it much easier for us to plan and build releases.

It is recommended to use `docker-compose` when running Pika, since plugins and
other supporting services can be run alongside it.

## Example

```yaml
version: '3'

services:
  pika:
    image: ghcr.io/picotorrent/pika:latest
    ports:
      - "1337:1337"
```

Run `docker-compose up` in the same directory as the `docker-compose.yml` file,
then head to [localhost:1337](http://localhost:1337) and you should see the
Pika web interface.
