# auto-mcs - Unraid Template

[![Unraid](https://img.shields.io/badge/Unraid-Community%20Apps-f15a2c?logo=unraid&logoColor=white)](https://unraid.net/community/apps)
[![Image](https://img.shields.io/badge/docker.io-macarooniman%2Fauto--mcs-2496ed?logo=docker&logoColor=white)](https://hub.docker.com/r/macarooniman/auto-mcs)
[![License](https://img.shields.io/github/license/YoshiroMaximus/automcs-unraid-template)](LICENSE)

Unraid Community Apps template for [**auto-mcs**](https://www.auto-mcs.com/) — a cross-platform Minecraft server manager that creates and runs servers (Vanilla, Paper, Fabric, Forge, and more) in under a minute, with mod/plugin management, automatic backups, and a scripting console. This container exposes it as a browser-based web terminal — no desktop client needed.

## Install

Add this template URL manually (**Docker → Add Container → Template**):

```
https://raw.githubusercontent.com/YoshiroMaximus/automcs-unraid-template/main/auto-mcs.xml
```

Once this repo is accepted into Community Applications, you'll also be able to find it by searching **auto-mcs** in the **Apps** tab.

## ⚠️ Set a password

The template ships **no default password** — you must set `WEB_PASSWORD` at install (the upstream default is `auto-mcs`; don't use it). The web terminal grants a **root shell inside the container**, so keep it on your LAN unless you've secured it.

## Running more than one server

auto-mcs opens a **new port for every server you create** (25566, 25567, a Bedrock UDP port, etc.). With the default `bridge` network you'd have to add a matching port mapping for each one. If you plan to run multiple servers, set **Network Type → `host`** when adding the container — auto-mcs then binds ports directly on the host with nothing to remap.

> Host mode shares the Unraid host's network stack. Make sure the web UI / server ports don't clash with Unraid itself (80/443) or other containers.

## Config

| Setting | Default |
| --- | --- |
| App Data | `/mnt/user/appdata/auto-mcs` → `/root/.auto-mcs` |
| Web UI port | `8080/tcp` (ttyd web terminal) |
| Minecraft server port | `25565/tcp` |
| Telepath API port (optional) | `7001/tcp` |
| `WEB_USERNAME` | `root` |
| `WEB_PASSWORD` | *(none — you set it at install)* |

Notes:
- **25565** is the default port for the Minecraft server auto-mcs runs. If Crafty (or another server) already uses it, change the host port (e.g. `30000`). For more than one server, prefer `host` networking (see above).
- The **Web UI Port** container side must stay `8080` — change only the host side if `8080` is taken.
- **7001** (Telepath) is the optional remote-management API — only expose it if you use it, and keep it off your WAN.
- The container reports a healthcheck (TCP probe on the web port), so Unraid shows green/red status.

## Links

[Project](https://www.auto-mcs.com/) · [Source & issues](https://github.com/macarooni-man/auto-mcs) · `macarooniman/auto-mcs:latest`
