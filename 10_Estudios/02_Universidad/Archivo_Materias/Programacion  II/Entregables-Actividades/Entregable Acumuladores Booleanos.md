

# Matrices en Java — Ejercicios con acumuladores booleanos
## Conceptos clave usados en todos los ejercicios

Todos los ejercicios siguen la misma filosofía: **acumuladores booleanos** en lugar de `return` o `break` dentro de los loops.

|Patrón|Uso|Arranca en|
|---|---|---|
|`acum = acum && condicion`|Verificar que **todos** cumplan|`true`|
|`acum = acum \| condicion`|Verificar que **alguno** cumpla|`false`|

La condición de corte anticipado en el `for` (`&& !acum` o `&& acum`) evita iteraciones innecesarias una vez que el resultado ya está determinado.

---

## Ejercicio 1 — `todosMultiplosEnAlgunaFila`

### Enunciado

Dada una matriz de enteros y un número, verificar si **existe alguna fila** donde **todos** sus elementos sean múltiplos del número. Si la matriz está vacía o el número no es positivo, devuelve `false`.

### Flujo

```
Entrada: mat[][], num
    │
    ├─ ¿mat vacía o num ≤ 0? ──► false
    │
    └─ Por cada fila i (mientras !hayFilaValida)
            │
            └─ todasMultiplos = true
               Por cada elemento j
                   todasMultiplos = todasMultiplos && (mat[i][j] % num == 0)
               │
               hayFilaValida = hayFilaValida || todasMultiplos
    │
    └─► return hayFilaValida
```

### Acumuladores

```
todasMultiplos  →  &&  →  arranca en true   →  ¿todos los elem de la fila son múltiplos?
hayFilaValida   →  ||  →  arranca en false  →  ¿alguna fila cumplió?
```

### Código

```java
public boolean todosMultiplosEnAlgunaFila(int[][] mat, int num) {
    if (mat == null || mat.length == 0 || num <= 0) {
        return false;
    }

    boolean hayFilaValida = false;

    for (int i = 0; i < mat.length && !hayFilaValida; i++) {
        if (mat[i] == null || mat[i].length == 0) continue;

        boolean todasMultiplos = true;

        for (int j = 0; j < mat[i].length; j++) {
            todasMultiplos = todasMultiplos && (mat[i][j] % num == 0);
        }

        hayFilaValida = hayFilaValida || todasMultiplos;
    }

    return hayFilaValida;
}
```

### Ejemplo

```
Matriz:          num = 3
2  4  3
6  3  9   ← fila 1: 6%3=0, 3%3=0, 9%3=0 → todasMultiplos=true → hayFilaValida=true
6  2  7

num = 2 → ninguna fila tiene todos múltiplos de 2 → false
```

---

## Ejercicio 2 — `hayInterseccionPorFila`

### Enunciado

Dadas 2 matrices, verificar si **todas las filas** tienen intersección fila a fila (al menos un elemento en común entre mat1[i] y mat2[i]). Si tienen distinta cantidad de filas o alguna está vacía, devuelve `false`.

### Flujo

```
Entrada: mat1[][], mat2[][]
    │
    ├─ ¿alguna vacía o null? ──► false
    ├─ ¿distinta cant. de filas? ──► false
    │
    └─ Por cada fila i (mientras todasFilasConInterseccion)
            │
            └─ filaConInterseccion = false
               Por cada elem j de mat1[i] (mientras !filaConInterseccion)
                   Por cada elem k de mat2[i] (mientras !filaConInterseccion)
                       filaConInterseccion = filaConInterseccion || (mat1[i][j] == mat2[i][k])
               │
               todasFilasConInterseccion = todasFilasConInterseccion && filaConInterseccion
    │
    └─► return todasFilasConInterseccion
```

### Acumuladores

```
filaConInterseccion          →  ||  →  arranca en false  →  ¿algún par de elem coincide en esta fila?
todasFilasConInterseccion    →  &&  →  arranca en true   →  ¿todas las filas tuvieron intersección?
```

### Código

```java
public boolean hayInterseccionPorFila(int[][] mat1, int[][] mat2) {
    if (mat1 == null || mat2 == null || mat1.length == 0 || mat2.length == 0) {
        return false;
    }
    if (mat1.length != mat2.length) {
        return false;
    }

    boolean todasFilasConInterseccion = true;

    for (int i = 0; i < mat1.length && todasFilasConInterseccion; i++) {
        boolean filaConInterseccion = false;

        for (int j = 0; j < mat1[i].length && !filaConInterseccion; j++) {
            for (int k = 0; k < mat2[i].length && !filaConInterseccion; k++) {
                filaConInterseccion = filaConInterseccion || (mat1[i][j] == mat2[i][k]);
            }
        }

        todasFilasConInterseccion = todasFilasConInterseccion && filaConInterseccion;
    }

    return todasFilasConInterseccion;
}
```

### Ejemplo

```
mat1          mat2
1  2  3       4  5  6  7
3  4  5  6    8  7  8  9
7  8  9  0    3  5  2  4  7  1  2

Fila 0: {1,2,3} ∩ {4,5,6,7}     = {}    → false → todasFilas=false → corta
Fila 0: {1,2,3} ∩ {4,5,6,7,8}   = {4}?  → no... depende de los valores
→ ver enunciado: mat1 y mat2 → true ({4}, {3,5}, {7})
→ mat1 y mat3 → false (filas 2 y 3 sin intersección)
```

---

## Ejercicio 3 — `algunaFilaSumaMasQueLaColumna`

### Enunciado

Dada una matriz y un índice de columna, verificar si **existe alguna fila** cuya suma sea mayor estricto que la suma de esa columna. Si el índice es inválido o la matriz está vacía, devuelve `false`.

### Flujo

```
Entrada: mat[][], nColum
    │
    ├─ ¿mat vacía o null? ──► false
    ├─ ¿nColum fuera de rango? ──► false
    │
    ├─ Paso 1: sumar columna nColum
    │       sumaColumna = Σ mat[i][nColum]  para todo i
    │
    └─ Paso 2: buscar fila con suma mayor
            hayFilaMayor = false
            Por cada fila i (mientras !hayFilaMayor)
                sumaFila = Σ mat[i][j]  para todo j
                hayFilaMayor = hayFilaMayor || (sumaFila > sumaColumna)
    │
    └─► return hayFilaMayor
```

### Acumuladores

```
sumaColumna   →  +   →  arranca en 0      →  suma total de la columna (no booleano)
sumaFila      →  +   →  arranca en 0      →  suma de la fila actual (no booleano)
hayFilaMayor  →  ||  →  arranca en false  →  ¿alguna fila superó la suma de la columna?
```

> Este ejercicio combina **acumuladores numéricos** (para las sumas) con un **acumulador booleano** (para el resultado final).

### Código

```java
public boolean algunaFilaSumaMasQueLaColumna(int[][] mat, int nColum) {
    if (mat == null || mat.length == 0) {
        return false;
    }
    if (nColum < 0 || nColum >= mat[0].length) {
        return false;
    }

    int sumaColumna = 0;
    for (int i = 0; i < mat.length; i++) {
        sumaColumna = sumaColumna + mat[i][nColum];
    }

    boolean hayFilaMayor = false;

    for (int i = 0; i < mat.length && !hayFilaMayor; i++) {
        int sumaFila = 0;

        for (int j = 0; j < mat[i].length; j++) {
            sumaFila = sumaFila + mat[i][j];
        }

        hayFilaMayor = hayFilaMayor || (sumaFila > sumaColumna);
    }

    return hayFilaMayor;
}
```

### Ejemplo

```
Matriz:
2   4   3   → sumaFila = 9
5   8   9   → sumaFila = 22
6   2  12   → sumaFila = 20

Columna 0: {2, 5, 6} → sumaColumna = 13
  fila 0: 9  > 13? no
  fila 1: 22 > 13? sí → hayFilaMayor = true ✓

Columna 2: {3, 9, 12} → sumaColumna = 24
  fila 0: 9  > 24? no
  fila 1: 22 > 24? no
  fila 2: 20 > 24? no → false ✓
```

---

## Ejercicio 4 — `hayInterseccionPorColumna`

### Enunciado

Dadas 2 matrices, verificar si **todas las columnas** tienen intersección columna a columna (al menos un elemento en común entre la columna j de mat1 y la columna j de mat2). Si tienen distinta cantidad de columnas o alguna está vacía, devuelve `false`.

### Flujo

```
Entrada: mat1[][], mat2[][]
    │
    ├─ ¿alguna vacía o null? ──► false
    ├─ ¿distinta cant. de columnas? ──► false
    │
    └─ Por cada columna j (mientras todasColumnasConInterseccion)
            │
            └─ columnaConInterseccion = false
               Por cada fila i de mat1 (mientras !columnaConInterseccion)
                   Por cada fila k de mat2 (mientras !columnaConInterseccion)
                       columnaConInterseccion = columnaConInterseccion || (mat1[i][j] == mat2[k][j])
               │
               todasColumnasConInterseccion = todasColumnasConInterseccion && columnaConInterseccion
    │
    └─► return todasColumnasConInterseccion
```

### Acumuladores

```
columnaConInterseccion        →  ||  →  arranca en false  →  ¿algún par de elem coincide en esta columna?
todasColumnasConInterseccion  →  &&  →  arranca en true   →  ¿todas las columnas tuvieron intersección?
```

### Diferencia clave con Ejercicio 2

```
Ejercicio 2 (por fila):    for j (columnas de mat1[i])  vs  for k (columnas de mat2[i])
                           índice fijo: i  →  varía: j, k

Ejercicio 4 (por columna): for i (filas de mat1)        vs  for k (filas de mat2)
                           índice fijo: j  →  varía: i, k
```

### Código

```java
public boolean hayInterseccionPorColumna(int[][] mat1, int[][] mat2) {
    if (mat1 == null || mat2 == null || mat1.length == 0 || mat2.length == 0) {
        return false;
    }
    if (mat1[0].length != mat2[0].length) {
        return false;
    }

    boolean todasColumnasConInterseccion = true;

    for (int j = 0; j < mat1[0].length && todasColumnasConInterseccion; j++) {
        boolean columnaConInterseccion = false;

        for (int i = 0; i < mat1.length && !columnaConInterseccion; i++) {
            for (int k = 0; k < mat2.length && !columnaConInterseccion; k++) {
                columnaConInterseccion = columnaConInterseccion || (mat1[i][j] == mat2[k][j]);
            }
        }

        todasColumnasConInterseccion = todasColumnasConInterseccion && columnaConInterseccion;
    }

    return todasColumnasConInterseccion;
}
```

---

## Resumen comparativo

|Ejercicio|Busca|Acumulador externo|Acumulador interno|
|---|---|---|---|
|1 — `todosMultiplosEnAlgunaFila`|**alguna** fila donde **todos** sean múltiplos|`\|` (alguna fila)|`&&` (todos los elem)|
|2 — `hayInterseccionPorFila`|**todas** las filas con intersección|`&&` (todas las filas)|`\|` (algún elem en común)|
|3 — `algunaFilaSumaMasQueLaColumna`|**alguna** fila con suma mayor|`\|` (alguna fila)|suma numérica|
|4 — `hayInterseccionPorColumna`|**todas** las columnas con intersección|`&&` (todas las columnas)|`\|` (algún elem en común)|

> **Regla nemotécnica:** si el enunciado dice _"existe alguna"_ → acumulador externo con `||` arrancando en `false`. Si dice _"todas"_ → acumulador externo con `&&` arrancando en `true`.