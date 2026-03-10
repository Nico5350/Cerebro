# Todos los libros leídos
Libros leídos y ordenados por nota de mayor a menor
```dataview
 TABLE 
	 ("![|60](" + portada + ")") AS "Portada",
	 saga AS "Saga", 
	 puntuacion AS "Nota", 
	 estado AS "Estado",
	 fecha_terminado AS "Fecha Finalizacion"
FROM "50_Personal" 
WHERE tipo = "libro" AND contains(estado, "Terminado") 
SORT puntuacion DESC
```
# Libros pendientes
```dataview
 TABLE 
	 saga AS "Saga", 
	 puntuacion AS "Nota", 
	 estado AS "Estado" 
FROM "50_Personal" 
WHERE tipo = "libro" AND contains(estado, "Pendiente") 
SORT puntuacion DESC
```

# Libros activos
```dataview
 TABLE 
	 saga AS "Saga", 
	 puntuacion AS "Nota", 
	 estado AS "Estado",
	 fecha_inicio AS "Fecha inicio" 
FROM "50_Personal" 
WHERE tipo = "libro" AND contains(estado, "Activo") 
SORT puntuacion DESC
```