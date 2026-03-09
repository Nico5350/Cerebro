---
materia:
estado:
  - 📖 Cursando
  - ✅ Finalizada
  - ⏳ Pendiente
cuatrimestre: 2026-1C
tags:
  - universidad
  - autodidacta
---
# 🎓 Materia: <% tp.file.title %>

> [!ABSTRACT] Información General
> - **Horario:** > - **Aula/Link:** > - **Fechas de Exámenes:** ---

---

## 📚 Biblioteca de Material (PDFs)
> [!abstract] Documentación y Guías de Estudio
```dataview
TABLE 
    fuente AS "Origen",
    tags AS "Etiquetas"
FROM "<% tp.file.folder() %>"
WHERE contains(tipo, "lectura_pdf")
SORT file.name ASC