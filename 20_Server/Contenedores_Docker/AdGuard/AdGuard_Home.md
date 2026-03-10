---
tipo: ficha_contenedor
servicio: AdGuard Home
ip_local: http://192.168.0.6
puertos: 80:80
estado: 🟢 Activo
tags:
  - infraestructura
  - HomeLab
fecha_montaje: 2026-02-09
---

# 🐳 Servicio: AdGuard Home


> [!INFO] Propósito
> Servicio de Adblock para la red domestica 


## ⚙️ Especificaciones Técnicas
- **Imagen:** - adguard/adguardhome:latest
- **Red:** Bridge (con mapeo estricto de puertos)
- **IP/URL:** `192.168.0.6` (Panel de Control)
- **Puertos:** `53:53` (DNS), `80:80` (WebUI), `3000:3000` (Setup)

## 📂 Persistencia (Volúmenes)
| Ruta en Host (Linux)          | Ruta en Contenedor | Descripción               |
| ----------------------------- | ------------------ | ------------------------- |
| `/home/nicoserver/docker/...` | `/config`          | Archivos de configuración |
|                               |                    |                           |

## 📜 Docker Compose
```yaml
services:
  adguardhome:
    image: adguard/adguardhome:latest
    container_name: adguardhome
    restart: unless-stopped
    ports:
      - "53:53/tcp"
      - "53:53/udp"
      - "80:80/tcp"
      - "3000:3000/tcp"
      - "443:443/tcp"
      - "443:443/udp"
    volumes:
      - /home/nicoserver/data/adguard/work:/opt/adguardhome/work
      - /home/nicoserver/data/adguard/conf:/opt/adguardhome/conf
```

## Comandos Basicos
> [!INFO] Comandos
> docker logs -f --tail 50 adguardhome 
> docker restart adguardhome
