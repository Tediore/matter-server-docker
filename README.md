# Matter Server Container (DEPRECATED)

## About

**This has been deprecated in favor of the [official Home Assistant Matter server repo](https://github.com/home-assistant-libs/python-matter-server)**. To build the official container image, follow these steps:

1. `git clone https://github.com/home-assistant-libs/python-matter-server`
2. `cd python-matter-server`
3. `docker build . -t matter-server -f Dockerfile.dev`

Example docker-compose.yaml:
```yaml
  matter-server:
    image: matter-server:latest # the image that you built in the steps above
    container_name: matter-server
    volumes:
    - /opt/matter-server/data:/data # replace /opt/matter-server with whatever path you want
    restart: unless-stopped
    network_mode: host
```

Please note that, per the official HA Matter server repo, the containerized version outside of HA OS is meant for development and is not for end user support. **Please do not submit issues to that repo that aren't related to development of the Matter server.**

<br> 
=============================================

Original README:

This is a fork of the [Matter Server add-on](https://github.com/home-assistant/addons/tree/master/matter_server) for Home Assistant designed to be run standalone in a container for HA Container and HA Core. It runs and is able to be connected to Home Assistant via the Matter integration, but I don't have any Matter devices, so I can't confirm that this works. That's up to you to do and let me know if it doesn't!

Matter (formerly known as Connected Home over IP or CHIP) is an IPv6 based smart home standard. This provides a Matter Controller which allows you to commission and control of Matter devices. The matching Home Assistant integration communicates via WebSocket with this server.

[aarch64-shield]: https://img.shields.io/badge/aarch64-yes-green.svg
[amd64-shield]: https://img.shields.io/badge/amd64-yes-green.svg

## How to run
**docker-compose**

```yaml
  matter-server:
    image: tediore/matter-server:amd64 # or aarch64 depending on your host platform
    container_name: matter-server
    volumes:
    - /etc/matter-server/root:/root # replace /etc/matter-server with whatever path you want
    - /etc/matter-server/data:/data # ditto
    restart: unless-stopped
    network_mode: host
```
