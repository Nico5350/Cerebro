---

## fecha: 2026-03-19 materia: Programación II etiquetas: [ "#ungs", "#programacion-2", "#java", "#oop", "#proyecto" ] tipo: proyecto_activo

# 💼 Sistema de Gestión de RRHH

> [!INFO] Sobre el proyecto Proyecto práctico de Programación II para aplicar OOP, TADs, Acumuladores Booleanos, Árboles y Complejidad en Java.

---

## 🗂️ Estructura del proyecto

```
sistemaRRHH/
├── modelos/
│   ├── Empleado.java        ✅ Implementado
│   ├── Departamento.java    ✅ Implementado
│   └── Gerente.java         ⏳ Pendiente
├── tads/
│   ├── Cola.java            ⏳ Pendiente
│   ├── NodoCola.java        ⏳ Pendiente
│   ├── Pila.java            ⏳ Pendiente
│   └── NodoPila.java        ⏳ Pendiente
├── arbol/
│   ├── ArbolOrganigrama.java ⏳ Pendiente
│   └── NodoArbol.java        ⏳ Pendiente
└── main/
    └── Main.java             ⏳ Pendiente
```

---

## 📊 Estado del proyecto

|Clase|Paquete|Estado|Notas|
|---|---|---|---|
|`Empleado`|`modelos`|✅ Listo|Completo|
|`Departamento`|`modelos`|✅ Listo|Completo|
|`Gerente`|`modelos`|⏳ Pendiente|Definir herencia vs composición|
|`Cola` + `NodoCola`|`tads`|⏳ Pendiente|—|
|`Pila` + `NodoPila`|`tads`|⏳ Pendiente|—|
|`ArbolOrganigrama` + `NodoArbol`|`arbol`|⏳ Pendiente|—|
|`Main`|`main`|⏳ Pendiente|—|

---

## ✅ Progreso actual

### `Empleado.java`

- Atributos: `nombre`, `apellido`, `dni`, `id`
- Contador estático global para IDs automáticos
- Getters y setters
- `toString()` con `@Override`

### `Departamento.java`

- Lista privada de empleados
- `agregarEmpleado()` — agrega un empleado a la lista
- `eliminarEmpleado()` — búsqueda por ID + eliminación
- `getCantEmpleados()` — retorna el tamaño de la lista
- `toString()` con `@Override`

---

## 🔜 Próximos pasos

- [ ] **Clase `Gerente`** — decidir diseño:

> [!QUESTION] ¿Herencia o Composición? **Herencia** → `Gerente extends Empleado`
> 
> - ✅ Gerente ES un Empleado → relación natural
> - ✅ Reutiliza atributos y métodos directamente
> - ❌ Menos flexible si Gerente cambia mucho en el futuro
> 
> **Composición** → `Gerente` tiene un atributo `Empleado`
> 
> - ✅ Más flexible y desacoplado
> - ❌ Más código, relación menos intuitiva
> 
> 💡 Para este proyecto **herencia** es probablemente la opción más limpia.

- [ ] Implementar TADs: `Cola` y `Pila` con sus nodos
- [ ] Implementar `ArbolOrganigrama` para representar la jerarquía
- [ ] Conectar todo en `Main.java`

---

## 📚 Conceptos aplicados

|Concepto|Dónde se aplica|
|---|---|
|OOP / Herencia|`Gerente extends Empleado`|
|Encapsulamiento|Atributos privados + getters/setters|
|Static|Contador de IDs en `Empleado`|
|TADs|`Cola` y `Pila` en paquete `tads`|
|Árbol|`ArbolOrganigrama` para jerarquía de la empresa|
|Acumuladores|Búsqueda y filtros sobre listas de empleados|

---

_Ver también: [[09-03-2026 Acumuladores y Matrices]] | [[17-03-2026 Complejidad computacional]] | [[Parcial_Info_ProgII]]_