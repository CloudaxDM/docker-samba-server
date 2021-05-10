# Samba Server Container

[![Docker Pulls](https://img.shields.io/docker/pulls/cloudax/samba-server.svg)](https://hub.docker.com/r/cloudax/samba-server/)
[![Docker Stars](https://img.shields.io/docker/stars/cloudax/samba-server.svg)](https://hub.docker.com/r/cloudax/samba-server/)
[![Docker Build](https://img.shields.io/docker/automated/cloudax/samba-server.svg)](https://hub.docker.com/r/cloudax/samba-server/)
[![Docker Build Status](https://img.shields.io/docker/build/cloudax/samba-server.svg)](https://hub.docker.com/r/cloudax/samba-server/)

[Samba 4](https://www.samba.org/) server running under [s6 overlay](https://github.com/just-containers/s6-overlay) on [Alpine Linux](https://hub.docker.com/_/alpine/). Runs both `smbd` and `nmbd` services.

## Configuration

See [example directory](https://github.com/CloudaxDM/docker-samba-server/tree/master/example) for sample config file.

## Quickstart

```yml
samba:
  image: cloudax/samba-server


  volumes:
    # You must provide a Samba config file
    - ./smb.conf:/etc/samba/smb.conf

    # Shares
    - ~/projects:/mnt/projects
    - ~/videos:/mnt/videos:ro

  ports:
    - "137:137/udp"
    - "138:138/udp"
    - "139:139/tcp"
    - "445:445/tcp"

  environment:
    - USERNAME=youruser
    - PASSWORD=yourpw
```
