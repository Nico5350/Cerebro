---
tipo: evento
subtipo: parcial
title: "Parcial: <% tp.file.title %>"
allDay: true
date: <% tp.date.now("YYYY-MM-DD") %>
materia: 
estado_estudio: 
	- 🔴 Pendiente 
	- 🟡 Repasando 
	- 🟢 Listo
tags: [universidad, examen]
---
# 📝 Parcial: <% tp.file.title %>

> [!INFO] Detalles del Examen
> - **Materia:** [[<% tp.frontmatter.materia %>]]
> - **Fecha:** <% tp.frontmatter.date %>
> - **Estado:** <% tp.frontmatter.estado_estudio %>

---

## 📚 Temario a Estudiar
- [ ] 
- [ ] 
- [ ] 

## 🔗 Recursos Relacionados
- **PDFs:** - **Apuntes:** ---
[[00_Inicio|⬅️ Volver al Inicio]]