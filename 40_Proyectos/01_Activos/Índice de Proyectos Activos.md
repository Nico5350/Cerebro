---
tipo: indice
area: 
tags: [moc, organizacion]
---
# 🗺️ Índice de: <% tp.file.title %>

> [!ABSTRACT] Resumen del Área
> Describe brevemente qué contiene este índice y cuál es su función principal en tu cerebro digital.

---

## 🏗️ Estructura Principal
> [!MAP] Notas Raíz
> - [[00_Inicio|⬅️ Volver al Panel de Control]]
> -  [[Bitacora WebVida]]
> - [[Bitacora Bot Discord]]

---

## 📊 Vista Detallada (Dataview)
```dataview
TABLE 
    tags AS "Etiquetas",
    fecha_creacion AS "Creado"
FROM "<% tp.file.folder() %>"
WHERE file.name != this.file.name
SORT file.mtime DESC