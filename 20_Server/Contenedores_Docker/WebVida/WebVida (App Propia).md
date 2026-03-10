---
tipo: ficha_contenedor
servicio: WebVida / AppVida
ip_local:
puertos:
estado:
  - Proyecto Personal / En desarrollo
tags:
  - infraestructura
  - HomeLab
fecha_montaje: 2026-02-09
---
# 🐳 Servicio: AppVida

> [!INFO] Propósito
> App para detallar el dia a dia de mi vida o la de alguien mas 

## ⚙️ Especificaciones Técnicas
- **Imagen:** - **Red:** (Bridge / Host / MacVlan)
- **IP/URL:** `undefined`
- **Puertos:** `undefined`

## 📂 Persistencia (Volúmenes)
| Ruta en Host (Linux)     | Ruta en Contenedor | Descripción |
| ------------------------ | ------------------ | ----------- |
| /home/nicoserver/appvida |                    |             |
|                          |                    |             |

## 📜 Docker Compose
```yaml
services:
  webvida:
    build: /home/nicoserver/appvida  # Construye desde la carpeta local
    container_name: webvida
    restart: unless-stopped
    ports:
      - "5000:5000" # Ajustar según tu app
    volumes:
      - /home/nicoserver/appvida:/app # Mapeo para editar código en vivo
    environment:
      - FLASK_ENV=development # O production
```
## Comandos Basicos
> [!INFO] Comandos
> docker compose build webvida
> docker logs -f 
> docker exec -it webvida /bin/bash
	