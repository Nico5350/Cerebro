---
tipo: indice
area: índice de archivo de materias
tags:
  - moc
  - organizacion
---

# 🗺️ Índice de: índice de archivo de materias

> [!ABSTRACT] Resumen del Área
> Notas e información de la carpeta: **Archivo_Materias**

---

## 🏗️ Estructura Principal
- [[00_Inicio|⬅️ Volver al Panel de Control]]

---

## 📊 Vista Detallada (Dataview)
```dataview
TABLE 
    tags AS "Etiquetas",
    file.ctime AS "Creado"
FROM "Archivo_Materias"
WHERE file.name != this.file.name
SORT file.mtime DESC