---
tipo: evento
subtipo: medico
title: "Turno: <% tp.file.title %>"
date: <% tp.date.now("YYYY-MM-DD") %>
horario: <% tp.date.now("HH:mm") %>
lugar: 
allDay: false
tags: [personal, salud]
---
# 🏥 Turno Médico: <% tp.file.title %>

> [!IMPORTANT] Información del Turno
> - **📅 Fecha:** <% tp.frontmatter.date %>
> - **⏰ Horario:** <% tp.frontmatter.horario %>
> - **📍 Lugar:** <% tp.frontmatter.lugar %>

---

## 📝 Notas / Recordatorios
- (Ej: Ayuno, llevar estudios previos, etc.)

---
[[00_Inicio|⬅️ Volver al Inicio]]