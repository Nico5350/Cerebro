---
tipo: indice
area: Sin título
tags:
  - moc
  - organizacion
---
# 🗺️ Índice de: Estudios

> [!ABSTRACT] Carpetas

> [[Orga]]
> 

---

## 🏗️ Estructura Principal
- [[00_Inicio|⬅️ Volver al Panel de Control]]

---

## 📊 Vista Detallada (Dataview)
```dataview
TABLE 
    tags AS "Etiquetas",
    file.ctime AS "Creado"
FROM "10_Estudios"
WHERE file.name != this.file.name
SORT file.mtime DESC