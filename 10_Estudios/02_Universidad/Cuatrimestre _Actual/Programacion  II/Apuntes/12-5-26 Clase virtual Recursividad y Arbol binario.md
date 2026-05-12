## 2do Parcial:

TADS Objetos 1:30
- Diagrama de clase
- Constructores
- Resolver 2 métodos
- Conceptos a utilizar

Arboles 1:30
- Árbol Binario
- Árbol
- Peor caso 
- Recursividad

## Recursividad:
- Tiene uno o mas casos bases
- Se llama así mismo reduciendo el problema hasta llegar al caso base, llamada recursiva
- Todo algoritmo Recursivo se puede escribir de forma iterativa y viceversa
- SOLO VAMOS A USAR RECURSIVIDAD
### Algoritmos de recursividad
- Factorial
- Fibonacci
- Búsqueda binaria
- Insertar en una lista enlazada ordenada

```bash
int factorial(int n){
	if(n == 0) // caso base
		return 1;
		return n * factorial (n-1)	
}

### Fibonacci
int fib(int n){
	if (n<2)//f0 = 0 y f1 = 1
		return n;
	return fib(n-1) + fib (n-2)
}
### Busqueda Binaria
int busqBin(int[]A, int x){
	return busqBin(A,x,0,A.length - 1)
}
int 
### Insertar en lista ordenada

```
## Arboles
-Es una estructura de datos y usa recursividad
-Todos los datos se almacenan en Nodos y todos son accesibles desde el Nodo raíz
-Esta formado por nodos y hay un nodo raíz y luego sus hijos tienen herencia, siempre empezamos desde la raíz
### Como se forman los nodos:
un arbol constanta de un conjunto finito de elementos
- Nodo Raíz: el único sin padre
- Nodo Internos: Nodos con unos o mas hijos 
- Nodo Hoja: Nodos sin hijos

![[Pasted image 20260512100827.png]]
#### *Altura*: 
desde el nodo raíz a la hoja mas lejana
#### *Grado*:
cantidad máximas de nodos/hijos dsp de la raíz
#### *Niveles*
la raíz es nivel 1 y desde allí empieza a bajar, por ejemplos los hijos del nodo raíz serian el nivel 2

#### *Camino*:
Secuencia de nodos adyacentes para llegar de un nodo X a un nodo Y
#### *Rama*: 
Camino que comienza en la raíz y termina en una hoja
#### *Nivel*
todos los nodos que están a la misma distancia de la raíz