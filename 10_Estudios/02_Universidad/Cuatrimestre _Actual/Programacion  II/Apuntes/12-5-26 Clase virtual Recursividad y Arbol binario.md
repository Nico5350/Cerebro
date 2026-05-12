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
```bash
