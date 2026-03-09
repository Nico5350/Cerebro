---
tipo: proyecto
estado:
  - 🟢 Activo 
  - 🟡 Pausado 
  - ✅ Terminado
prioridad:
  - 🟡 Media 
  - 🔴 Alta 
  - 🔵 Baja
  - Terminado
fecha_inicio: <% tp.date.now("YYYY-MM-DD") %>
materia_o_area:
tags:
  - desarrollo
  - proyecto
---
# 🚀 Proyecto: <% tp.file.title %>

> [!ABSTRACT] Objetivo del Proyecto
> Descripción clara de qué se busca lograr con este proyecto.

---

## 🗺️ Planificación y Recursos
- **Repositorio/Ruta:** `C:\Users\Nico\Proyectos\...`
- **Stack Tecnológico:** (ej. Java, Assembly ARM, Docker)
- **Documentación Relacionada:** [[índice de Código]] | [[La Chiquitita]]

---

## 📋 Tablero de Tareas (Kanban)
> [!TODO] Pendientes Críticos
```dataview
TASK
FROM "<% tp.file.folder() %>"
WHERE !completed
GROUP BY file.name