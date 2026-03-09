---
tipo: ficha_contenedor
servicio:
ip_local:
puertos:
estado: 🟢 Activo
tags:
  - infraestructura 
  - HomeLab
fecha_montaje: <% tp.date.now("YYYY-MM-DD") %>
---
# 🐳 Servicio: <% tp.file.title %>

> [!INFO] Propósito
> Breve descripción de para qué sirve este contenedor en tu Home Lab.

## ⚙️ Especificaciones Técnicas
- **Imagen:** - **Red:** (Bridge / Host / MacVlan)
- **IP/URL:** `<% tp.frontmatter.ip_local %>`
- **Puertos:** `<% tp.frontmatter.puertos %>`

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
> Ingrese los comandos basicos para operar
