# 🗃️ TADs — Tipos Abstractos de Datos

> [!INFO] ¿Qué es un TAD? Un **Tipo Abstracto de Dato** define **qué datos** contiene y **qué operaciones** se pueden hacer, sin importar **cómo está implementado** internamente. Separa la interfaz del usuario de la implementación.

---

## 📦 1. Estructuras de Datos

### 🔲 Arreglo Estático

|Característica|Detalle|
|---|---|
|Tamaño|**Fijo**|
|Tipos de dato|Mismo tipo para todos|
|Memoria|Contigua|

|Operación|Complejidad|Detalle|
|---|---|---|
|Acceso por índice|O(1)O(1) O(1)|Acceso directo|
|Agregar al principio|O(n)O(n) O(n)|Hay que mover todos los elementos|
|Agregar al final (libre)|O(1)O(1) O(1)|Si no está lleno|
|Agregar al final (lleno)|O(n)O(n) O(n)|Hay que crear un arreglo más grande|
|Definir/modificar|O(1)O(1) O(1)|Directo por índice|
|Quitar|O(n)O(n) O(n)|Hay que mover los elementos posteriores|
|Buscar|O(n)O(n) O(n)|Hay que recorrer todo|

---

### 🔲 Matriz

Arreglo bidimensional con la misma cantidad de columnas por fila. Mismas características que el arreglo estático.

---

### 🔗 Tupla

|Característica|Detalle|
|---|---|
|Tamaño|**2 elementos fijos**|
|Tipos de dato|Pueden ser de **distinto tipo**|

|Operación|Complejidad|Detalle|
|---|---|---|
|Acceso|O(1)O(1) O(1)|Es uno o el otro|
|Definir|O(1)O(1) O(1)|Se cambia fácilmente|
|Agregar / Quitar|❌|No se puede|

> Útil cuando necesitamos relacionar 2 elementos de distinto tipo.

---

### 🔗 Lista Enlazada

|Característica|Detalle|
|---|---|
|Tamaño|**Dinámico**|
|Tipos de dato|Mismo tipo para todos|
|Memoria|**No contigua**|

|Operación|Complejidad|Detalle|
|---|---|---|
|Acceso por índice|O(n)O(n) O(n)|Hay que recorrer hasta la posición|
|Agregar al principio|O(1)O(1) O(1)||
|Agregar al final|O(n)O(n) O(n)|Hay que llegar hasta el último nodo|
|Definir|O(n)O(n) O(n)|Hay que llegar al nodo|
|Quitar primero|O(1)O(1) O(1)||
|Quitar otro|O(n)O(n) O(n)|Hay que llegar al nodo|
|Buscar|O(n)O(n) O(n)|Hay que recorrer toda la lista|

---

### 📚 Pila (Stack) — LIFO

> **Last In, First Out** — Último en entrar, primero en salir.

|Característica|Detalle|
|---|---|
|Tamaño|**Dinámico**|
|Acceso por índice|❌ No se puede|
|Definir|❌ No se puede|

|Operación|Complejidad|Detalle|
|---|---|---|
|`push` — agregar|O(1)O(1) O(1)|Solo en el tope|
|`pop` — quitar|O(1)O(1) O(1)|Solo el tope|
|Buscar|O(n)O(n) O(n)|Hay que desapilar todo|

**Analogía:** una pila de platos. Solo podés sacar el de arriba.

---

### 🚶 Cola (Queue) — FIFO

> **First In, First Out** — Primero en entrar, primero en salir.

|Característica|Detalle|
|---|---|
|Tamaño|**Dinámico**|
|Acceso por índice|❌ No se puede|
|Definir|❌ No se puede|

|Operación|Complejidad|Detalle|
|---|---|---|
|`enqueue` — agregar|O(1)O(1) O(1)|Solo al final|
|`dequeue` — quitar|O(1)O(1) O(1)|Solo del inicio|
|Buscar|O(n)O(n) O(n)|Hay que desencolar todo|

**Analogía:** una fila del banco. El primero que llega es el primero en ser atendido.

---

### #️⃣ Tabla de Hash

|Característica|Detalle|
|---|---|
|Tamaño|**Dinámico**|
|Acceso por índice|❌ Sin orden definido|

|Operación|Complejidad|Detalle|
|---|---|---|
|Agregar|O(1)O(1) O(1)||
|Agregar (tabla llena)|O(n)O(n) O(n)|Hay que agrandar la tabla|
|Quitar|O(1)O(1) O(1)|Busca por hash|
|Buscar|O(1)O(1) O(1)|Busca por hash|

> Depende de implementar una buena **función de hash**.

---

### 🔵 Conjunto (Set)

No permite elementos repetidos. No tiene orden.

|Operación|Complejidad|Con Hash|
|---|---|---|
|Agregar|O(n)O(n) O(n)|O(1)O(1) O(1)|
|Quitar|O(n)O(n) O(n)|O(1)O(1) O(1)|
|Buscar|O(n)O(n) O(n)|O(1)O(1) O(1)|

---

### 📖 Mapeo / Diccionario

Asocia una **clave** a un **valor**. No permite claves repetidas.

|Operación|Complejidad|Con Hash|
|---|---|---|
|Agregar|O(n)O(n) O(n)|O(1)O(1) O(1)|
|Definir (por clave)|O(n)O(n) O(n)|O(1)O(1) O(1)|
|Quitar|O(n)O(n) O(n)|O(1)O(1) O(1)|
|Buscar|O(n)O(n) O(n)|O(1)O(1) O(1)|

---

## 📊 2. Cuadro Comparativo

|Estructura|Tamaño|Agregar primero|Agregar|Acceder|Quitar|Buscar|
|---|---|---|---|---|---|---|
|Arreglo|Fijo|O(n)O(n) O(n)|O(n)O(n) O(n)|O(1)O(1) O(1)|O(n)O(n) O(n)|O(n)O(n) O(n)|
|Lista|Dinámico|O(1)O(1) O(1)|O(n)O(n) O(n)|O(n)O(n) O(n)|O(n)O(n) O(n)|O(n)O(n) O(n)|
|Pila|Dinámico|—|O(1)O(1) O(1)|—|O(1)O(1) O(1)*|O(n)O(n) O(n)|
|Cola|Dinámico|—|O(1)O(1) O(1)|—|O(1)O(1) O(1)*|O(n)O(n) O(n)|
|Conjunto|Dinámico|—|O(n)O(n) O(n)|—|O(n)O(n) O(n)|O(n)O(n) O(n)|
|Diccionario|Dinámico|—|O(n)O(n) O(n)|O(n)O(n) O(n)**|O(n)O(n) O(n)|O(n)O(n) O(n)|
|Hash|Dinámico|—|O(1)O(1) O(1)|—|O(1)O(1) O(1)|O(1)O(1) O(1)|
|Conjunto+Hash|Dinámico|—|O(1)O(1) O(1)|—|O(1)O(1) O(1)|O(1)O(1) O(1)|
|Dicc+Hash|Dinámico|—|O(1)O(1) O(1)|O(1)O(1) O(1)**|O(1)O(1) O(1)|O(1)O(1) O(1)|

> * En Pila se desapila el tope, en Cola se desencola el primero. ** Acceder por clave.

---

## 🏦 3. Entregable — TAD AtencionBancaria

> [!WARNING] Entrega obligatoria para el parcial **Fecha:** Martes 14/04/2026 **Modalidad:** Individual, **manuscrito en papel** con nombre, apellido y comisión. Es condición necesaria para presentarse al parcial. No es necesario aprobarla.

---

### 📋 Enunciado resumido

Un banco gestiona la atención al público con tres tipos de clientes:

|Tipo|Prioridad|
|---|---|
|Cliente corporativo|Alta — se llama **2 veces** por ciclo|
|Cliente particular|Media — se llama **1 vez** por ciclo|
|No cliente|Baja — se llama **1 vez** por ciclo|

**Ciclo de atención:** 2 corporativos → 1 particular → 1 no cliente → repetir.

Cada persona se identifica con: **DNI**, **tipo de cliente**. Cada empleado tiene: **legajo**, **nombre**, **número de caja**.

---

### ✅ Funcionalidades requeridas

1. Registrar el ingreso de una persona al banco
2. Registrar un empleado nuevo
3. Permitir que un empleado tome a la próxima persona (respetando prioridades) → devuelve el DNI
4. Consultar cuántas personas esperan por tipo
5. Determinar el total de personas en espera
6. Consultar si quedan personas por atender

---

### 🗂️ TADs involucrados

#### TAD `Persona`

**Datos:**

- `dni`: int
- `tipo`: String (`"corporativo"`, `"particular"`, `"noCliente"`)

**Operaciones:**

- `getDni()` → int
- `getTipo()` → String

---

#### TAD `Empleado`

**Datos:**

- `legajo`: int
- `nombre`: String
- `numeroCaja`: int

**Operaciones:**

- `getLegajo()` → int
- `getNombre()` → String
- `getNumeroCaja()` → int

---

#### TAD `ColaClientes`

Gestiona una cola FIFO para un tipo de cliente específico.

**Datos:**

- `cola`: Cola de Personas

**Operaciones:**

- `agregar(persona)` → agrega al final
- `atender()` → Persona — quita y devuelve el primero
- `getCantidad()` → int
- `estaVacia()` → boolean

---

#### TAD `AtencionBancaria` _(TAD Principal)_

**Datos:**

- `colaCorporativos`: ColaClientes
- `colarParticulares`: ColaClientes
- `colaNoClientes`: ColaClientes
- `empleados`: Lista de Empleados
- `contadorCiclo`: int — lleva cuenta del ciclo de atención

**Interfaz pública:**

java

```java
void registrarPersona(int dni, String tipo)
void registrarEmpleado(int legajo, String nombre, int numeroCaja)
int atenderProximo()           // punto d) — respeta el ciclo de prioridades
int getCantidadPorTipo(String tipo)
int getTotalEnEspera()         // punto d)
boolean hayPersonasEsperando()
```

**IREP:**

- `colaCorporativos`, `colaParticulares` y `colaNoClientes` nunca son null
- `contadorCiclo` vale 0, 1, 2 o 3 (0-1 = corporativo, 2 = particular, 3 = no cliente)
- Cada persona está en exactamente una de las tres colas

---

### 💻 Implementación — Puntos 3 y 5

**Punto 5 — `getTotalEnEspera()`:**

java

```java
public int getTotalEnEspera() {
    return colaCorporativos.getCantidad() 
         + colaParticulares.getCantidad() 
         + colaNoClientes.getCantidad();
}
```

**Punto 3 — `atenderProximo()`:**

java

```java
public int atenderProximo() {
    // Ciclo: 0,1 → corporativo | 2 → particular | 3 → no cliente
    Persona proxima = null;

    if (contadorCiclo < 2 && !colaCorporativos.estaVacia()) {
        proxima = colaCorporativos.atender();
    } else if (contadorCiclo == 2 && !colaParticulares.estaVacia()) {
        proxima = colaParticulares.atender();
    } else if (contadorCiclo == 3 && !colaNoClientes.estaVacia()) {
        proxima = colaNoClientes.atender();
    } else {
        // Si la cola del turno está vacía, buscar en las demás
        if (!colaCorporativos.estaVacia())
            proxima = colaCorporativos.atender();
        else if (!colaParticulares.estaVacia())
            proxima = colaParticulares.atender();
        else if (!colaNoClientes.estaVacia())
            proxima = colaNoClientes.atender();
    }

    contadorCiclo = (contadorCiclo + 1) % 4;
    return proxima != null ? proxima.getDni() : -1;
}
```

---

### 🔄 Parte 2 — Extensibilidad

Para incorporar nuevos tipos de cliente (jubilados, premium, preferencial) la solución más flexible es:

- Reemplazar los tipos fijos por una **estructura dinámica** como un `Diccionario<String, ColaClientes>` donde la clave es el tipo de cliente
- Las reglas de prioridad se pueden representar como una **lista ordenada de tipos** con su peso/frecuencia de atención
- Así agregar un nuevo tipo solo requiere agregar una entrada al diccionario y una regla de prioridad, sin modificar el código existente

> [!TIP] Ventaja Esta representación es más flexible porque respeta el principio **Open/Closed**: abierto para extensión, cerrado para modificación