---
tipo: ficha_contenedor
servicio: Portainer
ip_local: http://192.168.0.6:9000
puertos: 8000:8000, 9443:9443 (HTTPS)
estado: 🟢 Activo
tags:
  - infraestructura
  - HomeLab
fecha_montaje: 2026-02-09
---
# 🐳 Servicio: Portainer


> [!INFO] Propósito
> Interfaz gráfica Web (GUI) para gestionar Docker, contenedores, imágenes y redes.

## ⚙️ Especificaciones Técnicas
- **Imagen:** portainer/portainer-ce:latest
- **Red:** Bridge
- **IP/URL:** http://192.168.0.6:9000/
- **Puertos:** `8000:8000`, `9443:9443` (HTTPS)

## 📂 Persistencia (Volúmenes)
| Ruta en Host (Linux)            | Ruta en Contenedor | Descripción               |
| ------------------------------- | ------------------ | ------------------------- |
| /home/nicoserver/data/portainer | `/config`          | Archivos de configuración |
|                                 |                    |                           |

## 📜 Docker Compose
```yaml
services:
  portainer:
    image: portainer/portainer-ce:latest
    container_name: portainer
    restart: unless-stopped
    ports:
      - "8000:8000"
      - "9443:9443"
    volumes:
      - /var/run/docker.sock:/var/run/docker.sock
      - /home/nicoserver/data/portainer:/data
```
## Comandos Basicos
> [!INFO] Comandos
> docker logs -f portainer
	