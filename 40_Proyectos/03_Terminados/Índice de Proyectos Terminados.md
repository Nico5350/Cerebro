---
tipo: indice
area: Índice de Proyectos Terminados
tags:
  - moc
  - organizacion
---
# 🗺️ Índice de: Índice de Proyectos Terminados

> [!ABSTRACT] Resumen del Área
> Notas e información de la carpeta: **Terminados**

---

## 🏗️ Estructura Principal
- [[00_Inicio|⬅️ Volver al Panel de Control]]

---

## 📊 Vista Detallada 
```dataview
TABLE 
    tags AS "Etiquetas",
    file.ctime AS "Creado"
FROM "Terminados"
WHERE file.name != this.file.name
SORT file.mtime DESC