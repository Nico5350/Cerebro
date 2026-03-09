---
tipo: indice
area: índice materias actual
tags:
  - organizacion
---
# 🗺️ Índice de: <% tp.file.title %>

> [!ABSTRACT] Resumen del Área
> Notas e información de la carpeta: **<% tp.file.folder() %>**

---

## 🏗️ Estructura Principal
- [[00_Inicio|⬅️ Volver al Panel de Control]]

---

## 📊 Vista Detallada (Dataview)
```dataview
TABLE 
    estado AS "Estado",
    dias_cursada AS "Cursada"
FROM "10_Estudios/Universidad/Cuatrimestre_Actual"
WHERE tipo = "materia"