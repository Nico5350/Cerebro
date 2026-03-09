---
tipo: ficha_contenedor
servicio: Uptime Kuma (Monitoring)
ip_local: http://192.168.0.6:3001/
puertos: 3001:3001
estado: 🟢 Activo
tags:
  - infraestructura
  - HomeLab
fecha_montaje: 2026-02-09
---
# 🐳 Servicio: Sin título

> [!INFO] Propósito
> Monitorización de estado de servicios (Ping a Minecraft, HTTP a AdGuard) con alertas.

## ⚙️ Especificaciones Técnicas
- **Imagen:** louislam/uptime-kuma:1
- **Red:** Bridge
- **IP/URL:** http://192.168.0.6:3001/
- **Puertos:** 3001:3001

## 📂 Persistencia (Volúmenes)
| Ruta en Host (Linux)              | Ruta en Contenedor | Descripción               |
| --------------------------------- | ------------------ | ------------------------- |
| /home/nicoserver/data/uptime-kuma | `/config`          | Archivos de configuración |
|                                   |                    |                           |

## 📜 Docker Compose
```yaml
services:
  uptime-kuma:
    image: louislam/uptime-kuma:1
    container_name: uptime-kuma
    restart: unless-stopped
    ports:
      - "3001:3001"
    volumes:
      - /home/nicoserver/data/uptime-kuma:/app/data
```
## Comandos Basicos
> [!INFO] Comandos
> docker logs -f uptime-kuma
> docker logs -f uptime-kuma
