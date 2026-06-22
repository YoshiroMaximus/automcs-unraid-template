# auto-mcs - Unraid Template

[![Unraid](https://img.shields.io/badge/Unraid-Community%20Apps-f15a2c?logo=unraid&logoColor=white)](https://unraid.net/community/apps)
[![Made with Python](https://img.shields.io/badge/Made%20with-Python-3776AB?logo=python&logoColor=white)](https://www.python.org/)
[![Image](https://img.shields.io/badge/docker.io-macarooniman%2Fauto--mcs-2496ed?logo=docker&logoColor=white)](https://hub.docker.com/r/macarooniman/auto-mcs)
[![License](https://img.shields.io/github/license/YoshiroMaximus/automcs-unraid-template)](LICENSE)

Unraid Community Apps template for [**auto-mcs**](https://www.auto-mcs.com/) — a cross-platform Minecraft server manager that creates and runs servers (Vanilla, Paper, Fabric, Forge, and more) in under a minute. Runs as a browser-based web terminal; no desktop client needed.

> 🔑 **Set a password.** No default ships — you set `WEB_PASSWORD` at install. The web terminal is a root shell inside the container, so use a strong one and keep it on your LAN.

## Install

Search **auto-mcs** in Community Apps, or add this template URL manually (**Docker → Add Container → Template**):

```
https://raw.githubusercontent.com/YoshiroMaximus/automcs-unraid-template/main/auto-mcs.xml
```

## Networking

auto-mcs opens a new port for every server you create. With the default `bridge` network you'd add a port mapping for each one — so if you plan to run more than one server, set **Network Type → `host`** when adding the container and auto-mcs binds them directly, nothing to remap.

Watch for clashes with Unraid's own ports (80/443) when using host mode.

## Config

| Setting | Default |
| --- | --- |
| Data | `/mnt/user/appdata/auto-mcs` → `/root/.auto-mcs` |
| Web UI port | `8080/tcp` (ttyd terminal) |
| Minecraft port | `25565/tcp` |
| Telepath API (optional) | `7001/tcp` |
| `WEB_USERNAME` | `root` |
| `WEB_PASSWORD` | *(set at install)* |

Tip: if Crafty (or another server) already uses `25565`, change the host port (e.g. `30000`). Leave the Web UI container side at `8080`.

## Links

[Project](https://www.auto-mcs.com/) · [Source & issues](https://github.com/macarooni-man/auto-mcs) · `macarooniman/auto-mcs:latest`
