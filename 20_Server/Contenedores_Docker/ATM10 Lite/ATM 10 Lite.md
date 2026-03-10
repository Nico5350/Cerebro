---
tipo: ficha_contenedor
servicio: Netdata (Real-time Performance Monitoring)
ip_local: round-developments.gl.joinmc.link
puertos: "25566"
estado: 🟢 Activo
tags:
  - HomeLab
fecha_montaje: 2026-02-10
---
# 🐳 Servicio: ATM10 Lite

> [!INFO] Propósito
> Servidor de minecraft con el mod pack all the mods 10 (atm10)

## ⚙️ Especificaciones Técnicas
- **Imagen:** - **Red:** (Bridge / Host / MacVlan)
- **IP/URL:**  round-developments.gl.joinmc.link
- **Puertos:** 25566

## 📂 Persistencia (Volúmenes)
| Ruta en Host (Linux)   | Ruta en Contenedor | Descripción               |
| ---------------------- | ------------------ | ------------------------- |
| /home/nicoserver/atm10 | `/config`          | Archivos de configuración |
|                        |                    |                           |

## 📜 Docker Compose
```yaml
# Pega aquí el código de tu docker-compose.yml
```
## Comandos Basicos
> [!INFO] Comandos
> docker logs -f atm10
> ./stop-all.sh
