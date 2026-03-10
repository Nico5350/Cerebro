---
tipo: ficha_contenedor
servicio: Beszel
ip_local: http://192.168.0.6:8090/
puertos: "8090"
estado: 🟢 Activo
tags:
  - HomeLab
fecha_montaje: 2026-02-15
---
# 🐳 Servicio: **Beszel**

> [!INFO] Propósito
> Interfez grafica de navegador para analisis de rendimiento y parametros el homelab

## ⚙️ Especificaciones Técnicas
- **Imagen:** - **Red:** (Bridge / Host / MacVlan)
- **IP/URL:** http://192.168.0.6:8090/
- **Puertos:**  8090

## 📂 Persistencia (Volúmenes)
| Ruta en Host (Linux)       | Ruta en Contenedor | Descripción               |
| -------------------------- | ------------------ | ------------------------- |
| `/home/usuario/docker/...` | `/config`          | Archivos de configuración |
|                            |                    |                           |

## 📜 Docker Compose
```yaml
# Pega aquí el código de tu docker-compose.yml
```
## Comandos Basicos
> [!INFO] Comandos
> Ingrese los comandos basicos para operar
