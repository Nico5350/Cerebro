---
tipo: ficha_contenedor
servicio: Immich
ip_local: http://192.168.0.6:2283/
puertos: "2283"
estado: 🟢 Activo
tags:
  - HomeLab
fecha_montaje: 2026-02-15
---
# 🐳 Servicio: Immich

> [!INFO] Propósito
> Servicio similar a google fotos conectado a mi celular el cual guarda y ordena imagenes en el almacenamiento del homelab
> 

## ⚙️ Especificaciones Técnicas
- **Imagen:** - **Red:** (Bridge / Host / MacVlan)
- **IP/URL:** http://192.168.0.6:2283/
- **Puertos:** 2283

## 📂 Persistencia (Volúmenes)
| Ruta en Host (Linux) | Ruta en Contenedor | Descripción |
| --- | --- | --- |
| `/home/usuario/docker/...` | `/config` | Archivos de configuración |
| | | |

## 📜 Docker Compose
```yaml
# Pega aquí el código de tu docker-compose.yml
```
## Comandos Basicos
> [!INFO] Comandos
> EJECUTAR DENTRO DE CARPETA /DOCKER/IMMICH
> APAGAR  docker compose down
> PRENDER  docker compose up -d
> REINICIAR docker compose restart