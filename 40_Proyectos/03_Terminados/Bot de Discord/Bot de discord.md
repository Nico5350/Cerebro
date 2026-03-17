---
tipo: proyecto
estado:
  - ✅ Terminado
prioridad:
  - Terminado
fecha_inicio: 2026-02-11
materia_o_area: Bot Discord
tags:
  - proyecto
---
# 🚀 Proyecto: Bot de discord

> [!ABSTRACT] Objetivo del Proyecto
> Bot para el servidor de discord que permite manejar desde la distancia los servidores. Con comandos como: 
> !status podemos ver si hay algun servidor prendido.
> !atm podemos iniciar el servidor de atm y apagar cobbleverse al mismo tiempo
> !cobble iniciamos el server de cobbleverse y apagamos atm
> !stop apagamos los servidores o cualquiera que este andando.

---

## 🗺️ Planificación y Recursos
- **Repositorio/Ruta:** `C:\Users\Nico\Proyectos\...`
- **Stack Tecnológico:** (ej. Java, Assembly ARM, Docker)
- **Documentación Relacionada:** [[índice de Código]] | [[La Chiquitita]]
-

---
## Comandos
```bash
docker compose up -d --build (Rearmar/actualizar el bot)
docker logs -f mc_discord_bot(Ver los logs)
docker logs --tail 20 mc_discord_bot (Ultimas 20 lineas de logs)
docker restart mc_discord_bot Reiniciar bot por si se cae

```

---
## 📋 Tablero de Tareas (Kanban)
> [!TODO] Pendientes Críticos
```dataview
TASK
FROM "Bot de Discord"
WHERE !completed
GROUP BY file.name