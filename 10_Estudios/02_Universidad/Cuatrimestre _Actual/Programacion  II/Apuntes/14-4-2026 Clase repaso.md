# Acumuladores Booleanos
# Complejidad


# TADS
### Estructura de TADs

- ## 1 Especificacion:
	- TAD Principal
		- ### Datos:
			- Cliente, Persona
		 - ### Operaciones:
			 - registrarCliente()
		- ### IREP
	- Siguientes TADS secundarios
- ## 2 Interfaz Publica:
	- Van los metodos que sean publicos y que no correspondan a las tads anteriores
	- registrarCliente(dni,nombre...)

- ## 3 Estructura de Datos:
	- Estructuras de datos que sean mas eficientes que vamos a utilizar
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
- ## 4 Implementacion:
	2 Metodos y auxiliares ej registrarCliente(dni,nombre...) y hacemos el metodo completo