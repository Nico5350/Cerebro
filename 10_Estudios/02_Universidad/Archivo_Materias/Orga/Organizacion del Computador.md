---
materia: Orga
estado:
  - ✅ Terminado
cuatrimestre: 2025-2C
tags:
  - universidad
  - ungs
---
# 🎓 Materia: Sin título

> [!ABSTRACT] Información General
> - **Horario:** Mañana
> - **Aula/Link:** 7019
> - **Fechas de Exámenes:** 26/02/2026 

---



### 📚 Material de Estudio
> [!abstract] Documentación y Guías de Estudio
```dataview
LIST
FROM "10_Estudios/Universidad"
WHERE tipo = "lectura_pdf" AND (materia = "Orga" OR contains(materia, this.file.name))