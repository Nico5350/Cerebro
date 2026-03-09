---
tipo: indice
area: <% tp.file.title %>
tags: [moc, organizacion]
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
    tags AS "Etiquetas",
    file.ctime AS "Creado"
FROM "<% tp.file.folder() %>"
WHERE file.name != this.file.name
SORT file.mtime DESC