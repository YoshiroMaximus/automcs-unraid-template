# auto-mcs - Unraid Template

[![Unraid](https://img.shields.io/badge/Unraid-Community%20Apps-f15a2c?logo=unraid&logoColor=white)](https://unraid.net/community/apps)
[![Image](https://img.shields.io/badge/docker.io-macarooniman%2Fauto--mcs-2496ed?logo=docker&logoColor=white)](https://hub.docker.com/r/macarooniman/auto-mcs)
[![License](https://img.shields.io/github/license/YoshiroMaximus/automcs-unraid-template)](LICENSE)

Unraid Community Apps template for [**auto-mcs**](https://www.auto-mcs.com/) — a cross-platform Minecraft server manager that spins up Vanilla, Paper, Fabric, Forge (and more) servers in under a minute, with Modrinth mod/plugin browsing, automatic backups, and a scripting console. This container exposes it as a browser-based web terminal — no desktop client needed.

## Install

Search **auto-mcs** in Community Apps, or add this template URL manually (**Docker → Add Container → Template**):

```
https://raw.githubusercontent.com/YoshiroMaximus/automcs-unraid-template/main/auto-mcs.xml
```

## ⚠️ Change the default password

The default login is **`root` / `auto-mcs`**. Change `WEB_PASSWORD` (and ideally `WEB_USERNAME`) before exposing the container — the web terminal grants shell access inside the container. Keep it on your LAN unless you've secured it.

## Config

| Setting | Default |
| --- | --- |
| App Data | `/mnt/user/appdata/auto-mcs` → `/root/.auto-mcs` |
| Web UI port | `8080/tcp` (ttyd web terminal) |
| Minecraft server port | `25565/tcp` |
| Telepath API port (optional) | `7001/tcp` |
| `WEB_USERNAME` | `root` |
| `WEB_PASSWORD` | `auto-mcs` (**change this**) |

Notes:
- **25565** is the default port for the Minecraft server auto-mcs runs. If Crafty (or another server) already uses it, change the host port (e.g. `30000`). Add more port mappings for additional servers.
- If you change the **Web UI Port**, set the `WEB_PORT` variable to the same value (it's the port the UI listens on inside the container).
- **7001** (Telepath) is optional remote-management API — only expose it if you use it, and keep it off your WAN.

## Links

[Project](https://www.auto-mcs.com/) · [Source & issues](https://github.com/macarooni-man/auto-mcs) · `macarooniman/auto-mcs:latest`
