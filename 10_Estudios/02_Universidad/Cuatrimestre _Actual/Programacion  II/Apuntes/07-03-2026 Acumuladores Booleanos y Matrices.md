
> [!INFO] Temas de esta clase Repaso de arreglos y matrices, recorrido por filas y columnas, y acumuladores booleanos con operadores AND/OR.

> [!NOTE] Mis anotaciones de clase
> 
> - Las **variables externas** (parámetros) se reciben para evaluar otras estructuras como matrices
> - Usamos **AND** cuando queremos verificar TODO → inicializar el acumulador en `true`
> - Usamos **OR** cuando queremos verificar ALGUNO → inicializar el acumulador en `false`
> - Ejemplo B: el acumulador inicia en `false` porque verifica si **alguno** es par

---

## 📦 1. Arreglos

Un arreglo es una secuencia de elementos con o sin repetidos, de la forma:

$$arr = [arr_0,\ arr_1,\ \dots,\ arr_{n-1}]$$

```java
int[] arr = { 4, 3, 5, 9, 5 };

arr[0] == 4   // ✅
arr[2] == 5   // ✅
arr[5]        // ❌ ArrayIndexOutOfBoundsException
```

> [!WARNING] Índice fuera de rango Acceder a un índice que no existe lanza `ArrayIndexOutOfBoundsException`. El último índice válido siempre es `arr.length - 1`.

---

## 🔲 2. Matrices

Una matriz es una tabla bidimensional de $m$ filas y $n$ columnas ($m \times n$).

||Matemáticas|Programación|
|---|---|---|
|Índices|Desde 1|Desde 0|
|Elemento|$a_{ij}$|`mat[i][j]`|
|Primera celda|$a_{11}$|`mat[0][0]`|
|Última celda|$a_{mn}$|`mat[m-1][n-1]`|

### Creación en Java

```java
// Forma 1: con new
int CANT_FILAS = 2;
int CANT_COLUMNAS = 3;
int[][] matriz = new int[CANT_FILAS][CANT_COLUMNAS];
matriz[0][0] = 1; matriz[0][1] = 2; matriz[0][2] = 3;
matriz[1][0] = 4; matriz[1][1] = 5; matriz[1][2] = 6;

// Forma 2: literal (más compacta)
int[][] matriz2 = {
    {1, 2, 3},
    {4, 5, 6}
};
```

---

## 🔄 3. Recorrido de Matrices

### Por fila (primero filas, luego columnas)

```java
for (int f = 0; f < matriz.length; f++)
    for (int c = 0; c < matriz[0].length; c++)
        System.out.print(matriz[f][c] + " ");
```

**Traza de ejecución** con `{{1,2,3},{4,5,6}}`:

|f|c|Salida acumulada|
|---|---|---|
|0|0|`1`|
|0|1|`1 2`|
|0|2|`1 2 3`|
|1|0|`1 2 3 4`|
|1|1|`1 2 3 4 5`|
|1|2|`1 2 3 4 5 6`|

### Por columna (primero columnas, luego filas)

```java
for (int c = 0; c < matriz[0].length; c++)
    for (int f = 0; f < matriz.length; f++)
        System.out.print(matriz[f][c] + " ");
```

**Traza de ejecución** con `{{1,2,3},{4,5,6}}`:

|c|f|Salida acumulada|
|---|---|---|
|0|0|`1`|
|0|1|`1 4`|
|1|0|`1 4 2`|
|1|1|`1 4 2 5`|
|2|0|`1 4 2 5 3`|
|2|1|`1 4 2 5 3 6`|

> [!TIP] Diferencia clave Recorrido por **fila** → el índice de fila `f` va en el bucle externo.  
> Recorrido por **columna** → el índice de columna `c` va en el bucle externo.

---

## ✅ 4. Acumuladores Booleanos

### Definición

Un **acumulador booleano** es una variable que acumula un valor de verdad (`true`/`false`) durante la ejecución de un bucle, implementando una función booleana.

### Tablas de verdad

||a|b|`a \| b`|`a && b`|
|---|---|---|---|---|
|(1)|f|f|f|f|
|(2)|f|v|v|f|
|(3)|v|f|v|f|
|(4)|v|v|v|v|

---

## 🔑 5. Cuantificadores — La Regla de Oro

> [!IMPORTANT] Regla general **Para TODOS** los elementos → hipótesis `true`, acumular con `&&`  
> **Para ALGÚN** elemento → hipótesis `false`, acumular con `||`

|Cuantificador|Notación|`ret` inicial|Acumulación|
|---|---|---|---|
|Universal (∀)|${\forall x \in lista / P(x)} \equiv true$|`true`|`ret = ret && P(x)`|
|Existencial (∃)|${\exists x \in lista / P(x)} \equiv true$|`false`|`ret = ret \| P(x)`|

---

## 💡 6. Ejemplos

### Ejemplo 1 — ¿Toda la lista es par?

```
Arreglo A: [4 7 9 15 35 39]  →  false
Arreglo B: [4 8 10 2 12]     →  true
```

**Versión sin acumuladores:**

```java
boolean esPar(lista) {
    for (int i = 0; i < lista.size(); i++)
        if (!(par(lista[i])))
            return false;
    return true;
}
```

**Versión con acumuladores (preferida):**

```java
boolean esPar(lista) {
    boolean ret = true;  // ← inicia en true (∀)
    for (int i = 0; i < lista.size(); i++)
        ret = ret && par(lista[i]);
    return ret;
}
```

---

### Ejemplo 2 — ¿Lista par? + multiplicar todos por 2

El problema: necesitamos hacer las dos cosas en el mismo recorrido.

**Versión 2a — sin acumuladores (❌ incompleta):**

```java
// Si encuentra un impar, sale antes de multiplicar el resto
boolean esPar(lista) {
    for (int i = 0; i < lista.size(); i++) {
        if (!(par(lista[i]))) return false;
        lista[i] = lista[i] * 2;
    }
    return true;
}
```

**Versión 2b — sin acumuladores (❌ lógica incorrecta):**

```java
// Multiplicar por 2 hace que todos queden pares → siempre retorna true
for (int i = 0; i < lista.size(); i++) lista[i] = lista[i] * 2;
for (int i = 0; i < lista.size(); i++)
    if (!(par(lista[i]))) return false;
return true;
```

**Versión 2c — sin acumuladores (❌ costosa):**

```java
// Necesita clonar la lista → doble uso de memoria
copiaLista = lista.clonar();
for (int i = 0; i < lista.size(); i++) lista[i] = lista[i] * 2;
for (int i = 0; i < copiaLista.size(); i++)
    if (!(par(copiaLista[i]))) return false;
return true;
```

**Versión 2d — con acumuladores (✅ correcta y eficiente):**

```java
boolean esPar(lista) {
    boolean ret = true;  // ← acumulador inicia en true
    for (int i = 0; i < lista.size(); i++) {
        ret = ret && par(lista[i]);  // evalúa ANTES de modificar
        lista[i] = lista[i] * 2;
    }
    return ret;
}
```

> [!SUCCESS] ¿Por qué funciona? El acumulador evalúa la paridad del valor **original** antes de multiplicarlo, y al usar `&&`, una vez que `ret` se vuelve `false` no puede volver a `true`.

---

### Ejemplo 3 — ¿Algún número de la lista es par?

```
Arreglo A: [3 8 1 9 11]  →  true  (el 8 es par)
Arreglo B: [9 5 1 7 3]   →  false
```

**Sin acumuladores:**

```java
boolean algunPar(lista) {
    for (int i = 0; i < lista.size(); i++)
        if (par(lista[i])) return true;
    return false;
}
```

**Con acumuladores (preferida):**

```java
boolean algunPar(lista) {
    boolean ret = false;  // ← inicia en false (∃)
    for (int i = 0; i < lista.size(); i++)
        ret = ret || par(lista[i]);
    return ret;
}
```

---

## 🏋️ 7. Ejercicio de la clase

Función que devuelve `true` si la lista tiene **todos los números > 8** Y **algún número < 23**:

```java
public class Ppal {
    public static void main(String[] args) {
        Integer[] lista1 = {9, 10, 11};    // cumple  → true
        Integer[] lista2 = {90, 100, 110}; // no cumple → false

        System.out.println(todosMayor8(lista1) && algunoMenor23(lista1)); // true
        System.out.println(todosMayor8(lista2) && algunoMenor23(lista2)); // false
    }

    // ∀ → ret = true, acumula con &&
    static public boolean todosMayor8(Integer[] lista) {
        boolean ret = true;
        for (int i = 0; i < lista.length; i++)
            ret = ret && lista[i] > 8;
        return ret;
    }

    // ∃ → ret = false, acumula con ||
    static public boolean algunoMenor23(Integer[] lista) {
        boolean ret = false;
        for (int i = 0; i < lista.length; i++)
            ret = ret || lista[i] < 23;
        return ret;
    }
}
```

---

## 📋 8. Ejercicios de Matrices con Acumuladores

### A) `algunaFilaPar(int[][] mat)`

Devuelve `true` si **al menos una fila** tiene todos sus elementos pares. Si la matriz está vacía, devuelve `true`.

### B) `algunaColumnaPar(int[][] mat)`

Devuelve `true` si **al menos una columna** tiene todos sus elementos pares. Si la matriz está vacía, devuelve `true`.

> [!TIP] Pista Son problemas anidados: para cada fila/columna necesitás un acumulador AND (¿todos los elementos son pares?), y luego otro acumulador OR para saber si alguna fila/columna cumple la condición.

---

_Ver también: [[17-03-2026 Complejidad computacional]] | [[Programación II]]_