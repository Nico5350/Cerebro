
> [!INFO] El Problema de la Eficiencia Cuando creamos un algoritmo, no solo importa que sea correcto, sino también eficiente. Decimos que es "caro" respecto a los recursos que utiliza: **memoria** (Complejidad Espacial) y **tiempo de ejecución** (Complejidad Temporal). En esta materia nos centramos exclusivamente en la **Complejidad Temporal** por ser el recurso más crítico.

---

## 1. Conteo de Instrucciones

Como el tiempo en segundos depende del hardware de cada PC, medimos la complejidad contando la cantidad de **instrucciones atómicas** que ejecuta el algoritmo en función del tamaño de su entrada ($n$).

Se considera que las siguientes operaciones consumen **1 ciclo de procesador**:

| Tipo                        | Operadores                                               |
| --------------------------- | -------------------------------------------------------- |
| **Aritméticos**             | `+`, `-`, `*`, `/`, `%`, `++`, `--`                      |
| **Lógicos**                 | `&&`, `\|`, `!`                                          |
| **Comparaciones**           | <, >, <=, >=, !=, ==                                     |
| **Accesos**                 | Índice a arreglo (`arr[i]`) o propiedades (`arr.length`) |
| **Asignaciones y retornos** | `=` y `return`                                           |

### Ejemplos Prácticos de Conteo

**Ejemplo 1: Complejidad Constante $O(1)$**

Evaluar si una matriz está vacía. No depende del tamaño de la matriz.

```java
boolean estaVacia(int[][] mat) {
    return mat==null || mat.length==0 || mat[0].length==0;
    // 1 return + 3 == + 2 || + 2 .length + 1 acceso [0] = 9 operaciones
}
```

**Ejemplo 2: Dependiente de $n$**

Verificar si todos los elementos de un arreglo son pares. El tamaño de entrada es $n = arr.length$.

```java
boolean todosPares(int[] arr) {
    boolean sonTodosPares = true;           // 1 op
    for(int i=0; i<arr.length; i++)         // 1 + 2(n+1) + n = 3 + 3n
        sonTodosPares = sonTodosPares && arr[i]%2 == 0; // 5 * n
    return sonTodosPares;                   // 1 op
}
```

$$f(n) = 1 + [3 + 3n] + 5n + 1 \Rightarrow \mathbf{f(n) = 8n + 5}$$

---

##  2. Análisis de Casos: Mejor, Peor y Medio

El tiempo de ejecución puede variar drásticamente según cómo ingresen los datos.

> [!WARNING] El Peor Caso La cota asintótica generalmente busca definir el **peor comportamiento posible** de nuestro algoritmo para prevenir fallos críticos de rendimiento.

|Caso|Descripción|Ejemplo (Inserción)|
|---|---|---|
|**Peor caso**|Máxima cantidad de operaciones|Arreglo ordenado al revés → $O(n^2)$|
|**Mejor caso**|Mínima cantidad de operaciones|Arreglo ya ordenado → $O(n)$|
|**Caso promedio**|Datos en orden aleatorio|—|

---

##  3. Complejidad Asintótica (Notación Big O)

Consiste en calcular la complejidad temporal cuando $n$ tiende a infinito, prescindiendo de constantes multiplicativas y términos de menor orden.

**Definición Formal:**

$$f(n) \in O(g(n)) \Leftrightarrow \exists\ n_0, c \text{ tales que para todo } n > n_0:$$

$$f(n) < c \cdot g(n)$$

Donde $c$ es una constante multiplicativa y $n_0$ es el valor a partir del cual $g(n)$ siempre supera a $f(n)$.

### Jerarquía de Órdenes de Crecimiento

$$O(1) \le O(\log n) \le O(n) \le O(n \log n) \le O(n^2) \le O(n^3) \le O(2^n) \le O(n!) \le O(n^n)$$

### Álgebra de Órdenes

Reglas para simplificar el cálculo de funciones complejas:

|Regla|Fórmula|
|---|---|
|Eliminación de constantes|$O(k) = O(1)$ y $O(c \cdot f(n)) = O(f(n))$|
|Suma (Regla del Máximo)|$O(f(n) + g(n)) = O(\max{f(n), g(n)})$|
|Producto|$O(f(n)) \cdot O(g(n)) = O(f(n) \cdot g(n))$|

**Ejemplo de Álgebra:**

Dada $f(n) = 9n^2 + 10n + 7$:

$$O(9n^2 + 10n + 7)$$ $$= O(9n^2) + O(10n) + O(7)$$ $$= O(n^2) + O(n) + O(1)$$ $$= O(\max{n^2, n, 1}) = \mathbf{O(n^2)}$$

---

##  4. La Sumatoria de Gauss

Aparece cuando analizamos bucles anidados donde el bucle interno depende del contador del bucle externo (ej. `j < a.length - i`).

**Fórmula de Gauss:**

$$\sum_{i=1}^n i = \frac{n(n+1)}{2}$$

**Complejidad de la Sumatoria:**

$$O\left(\frac{1}{2} n(n+1)\right) = O(1) \cdot O(n) \cdot O(n) = \mathbf{O(n^2)}$$

---

##  5. Demostraciones Prácticas

### Caso A: Cálculo de Constantes

Demostrar que $f(n) = 8n^2 + 4n + 5 \in O(n^2)$. Buscamos $c$ y $n_0$:

|Término|Acotación|Se cumple para|
|---|---|---|
|$8n^2$|$\le 8n^2$|$n \ge 1$|
|$4n$|$\le 2n^2$|$n \ge 2$|
|$5$|$\le 1n^2$|$n \ge 3$|

Sumamos constantes: $8 + 2 + 1 \Rightarrow \mathbf{c = 11}$ Tomamos el $n_0$ más restrictivo: $\mathbf{n_0 = 3}$

> **Conclusión:** $8n^2 + 4n + 5 \le 11n^2$ para todo $n \ge 3$, por lo tanto es $\mathbf{O(n^2)}$.

### Caso B: Algoritmo de Burbujeo

|Versión|Función|Constante $c$|$n_0$|Complejidad|
|---|---|---|---|---|
|Ineficiente (bucle hasta `a.length - 1`)|$f(n) = 15n^2 + 5n + 1$|$c = 16$|$n_0 = 6$|$O(n^2)$|
|Optimizada (bucle hasta `a.length - i`)|$f(n) = 8n^2 + 3n - 5$|—|—|$O(n^2)$|

> Aunque la constante bajó casi a la mitad (de 15 a 8), por álgebra de órdenes ambas versiones son $\mathbf{O(n^2)}$.

---

## ANEXO: Tabla de Impacto de Tiempos

Para un procesador que ejecuta $10^6$ operaciones por segundo (1MHz):

|$n$|$O(n)$|$O(n \log n)$|$O(n^2)$|$O(2^n)$|$O(n!)$|
|---|---|---|---|---|---|
|10|$10^{-5}$ seg|$3.3 \cdot 10^{-5}$ seg|0.001 seg|0.001 seg|3.63 seg|
|50|$5 \cdot 10^{-5}$ seg|$2.8 \cdot 10^{-4}$ seg|0.0025 seg|Intratable|Intratable|
|$10^3$|0.001 seg|0.01 seg|1 seg|Intratable|Intratable|
|$10^6$|1 seg|19.9 seg|11.5 días|Intratable|Intratable|