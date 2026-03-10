---
tipo: indice
area: Inidice de Bitacoras
tags:
  - organizacion
---
# 🗺️ Índice de: Inidice de Bitacoras

> [!ABSTRACT] Resumen del Área
> Notas e información de la carpeta: **Bitacoras de Server**

---

## 🏗️ Estructura Principal
- [[00_Inicio|⬅️ Volver al Panel de Control]]

---

## 📊 Vista Detallada (Dataview)
```dataview
TABLE 
    tags AS "Etiquetas",
    file.ctime AS "Creado"
FROM "Bitacoras de Server"
WHERE file.name != this.file.name
SORT file.mtime DESC