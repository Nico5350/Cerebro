---
tipo: ficha_contenedor
servicio: Servidor de Minecraft
ip_local: las-decade.gl.joinmc.link
puertos: 25565:25565 (TCP/UDP)
estado: 🟢 Activo
tags:
  - HomeLab
fecha_montaje: 2026-02-09
---
# 🐳 Servicio: Servidor de Cobbleverse

> [!INFO] Propósito
> Contenedor que donde corre el servidor de minecraft de cobbleverse

## ⚙️ Especificaciones Técnicas
- **Imagen:** itzg/minecraft-server:java21
- **Red:** Bridge (Default)
- **IP/URL:** las-decade.gl.joinmc.link
- **Puertos:** `25565:25565` (TCP/UDP)

## 📂 Persistencia (Volúmenes)
| Ruta en Host (Linux)          | Ruta en Contenedor | Descripción               |
| ----------------------------- | ------------------ | ------------------------- |
| `/home/nicoserver/docker/...` | `/config`          | Archivos de configuración |
|                               |                    |                           |
|                               |                    |                           |

## 📜 Docker Compose
```yaml
services:
  cobbleverse:
    image: itzg/minecraft-server:java21
    container_name: cobbleverse
    restart: unless-stopped
    ports:
      - "25565:25565"
    environment:
      - EULA=TRUE
      - TYPE=FABRIC
      - VERSION=1.21.1
      - MEMORY=6G
      - UID=1000
      - GID=1000
      - USE_AIKAR_FLAGS=true
      - MODRINTH_PROJECTS=lithium,ferrite-core,modernfix,krypton,noisium
      - VIEW_DISTANCE=16
      - SIMULATION_DISTANCE=8
    volumes:
      - /home/nicoserver/data/minecraft:/data