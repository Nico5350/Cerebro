---
tipo: ficha_contenedor
servicio: Netdata (Real-time Performance Monitoring)
ip_local: http://192.168.0.6:19999/
puertos: 19999:19999
estado: 🟢 Activo
tags:
  - infraestructura
  - HomeLab
fecha_montaje: 2026-02-09
---
# 🐳 Servicio: NetData

> [!INFO] Propósito
> Monitorización granular de CPU, RAM, Discos y Contenedores en tiempo real.

## ⚙️ Especificaciones Técnicas
- **Imagen:** netdata/netdata
- **Red:** Host (Recomendado) o Bridge
- **IP/URL:** http://192.168.0.6:19999/
- **Puertos:** 19999:19999

## 📂 Persistencia (Volúmenes)
| Ruta en Host (Linux) | Ruta en Contenedor | Descripción |
| --- | --- | --- |
| `/home/usuario/docker/...` | `/config` | Archivos de configuración |
| | | |

## 📜 Docker Compose
```yaml
services:
  netdata:
    image: netdata/netdata
    container_name: netdata
    restart: unless-stopped
    ports:
      - "19999:19999"
    cap_add:
      - SYS_PTRACE # Vital para inspeccionar procesos
    security_opt:
      - apparmor:unconfined
    volumes:
      - /home/nicoserver/data/netdata/config:/etc/netdata
      - /home/nicoserver/data/netdata/lib:/var/lib/netdata
      - /home/nicoserver/data/netdata/cache:/var/cache/netdata
      - /etc/passwd:/host/etc/passwd:ro
      - /etc/group:/host/etc/group:ro
      - /proc:/host/proc:ro
      - /sys:/host/sys:ro
      - /etc/os-release:/host/etc/os-release:ro
      - /var/run/docker.sock:/var/run/docker.sock # Vital para ver nombres de containers
```
## Comandos Basicos
> [!INFO] Comandos
> docker exec -it netdata netdata-claim.sh -token [TU_TOKEN] -rooms [TU_ROOM] -url https://app.netdata.cloud (**Reclamar Nodo (Cloud):** Si reinstalas, necesitas el token de netdata.cloud)
> docker logs -f netdata
