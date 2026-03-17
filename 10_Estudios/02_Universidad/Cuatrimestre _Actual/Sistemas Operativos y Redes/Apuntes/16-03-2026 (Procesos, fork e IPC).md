## Utilizamos el lenguaje C

- Sistemas Batch el so ejecuta varios programas
- Sistema time-Shared , Varios usuarios ejecutan distintas tareas en la misma cpu

### Concepto de proceso :
programa en ejecucion secuencial, el programa es una entidad pasiva y el proceso una entidad activa.
el programa se convierte en proceso cuando se ejecuta, un programa puede ser varios procesos.
ejemplo un contador.

Interior de un proceso cargado en memoria. text section(codigo del programa),data section (variables globales),heap(contiene memoria dinámica durante el tiempo de ejecución) y stack ()
### Estados de un proceso(hay diagrama en [[]]):
- Nuevo proceso que se esta creando
- Listo proceso listo para ser ejecutado, esperando un procesador.
- Ejecutando: se le asigna un procesador y se ejecutan sus instrucciones
- Terminado:termina de ejecutarse
- Bloqueado evento de i/o
### Scheduler
### PCB (foto del proceso del momento)
ficha técnica de un proceso y estado actual
- estado del proceso : corriendo, esperando, etc
- programcounter : ubicación de la siguiente instrucción ejecutar
- registros: contenido de los registros
- informacion de scheduling: prioridad o planificador
- memoria: información de memoria asignada al proceso
- info de ejecución: clock transcurridos desde el inicio
- info de entradas y salidas: Dispositivos asignados al proceso

el control block sirve para el context switch
### Context Switch
Cuando hay una interrupcion o llamada del sistema guarda el estado del proceso en la pcb, para retomar la ejecucion desde ese punto. pasa entre proceso 0 y 1 dependiendo del scheduler, depende de la memoria son la cantidad de procesos.
el tiempo es determinado por el hardware, esto se considera tiempo ocioso porque no realiza ningún trabajo entre pcbs
### Operaciones con procesos 
el sistema debe proporcionar mecanismos para: creación de procesos y terminación de procesos.
### En linux:
- esta el task_struct no esta disponible para el usario pero si podemos acceder a: estados del proceso con cat/proc/<id_del_proceso>/status
### Creacion de procesos (Cont.): 
- se pueden crear procesos padres e hijos y estos pueden compartir todos los recursos  y comparten los subconjuntos del padre. Esto forma un arbol de proceso y se identifica con identificador de procesos (pid)
- padre e hijo no comparten recursos
-  opciones de ejecucion: se ejecutan concurrentemente y el padre espera que el hijo finalice su ejecucion.

cuando ejecutamos un fork() se crea el proceso hijo que empieza a ejecutar instrucciones en la sigueinte linea. Para saber si es el hijo o el padre hay que ver que devuelve una variable(el pid) , si es 0 es el hijo, si es mayo a 0 es el proceso padre.

## Programa C con fork() 
### Fin de un Proceso:
el proceso ejecuta su ultima instrucción y sale mediante la syscall exit()
- retorna el estado del hijo al padre
-  se reasigna los recursos al SO
el padre puede terminar la ejecución utilizando abort por las siguientes razones:
- el hijo supera los recursos
- la tarea asignada al hijo ya no es necesaria
- el padre esta retirado y los SO no permiten que el hijo continué
-  *termina en cascada
- el padre puede esperar la terminacion de un proceso hijo con wait()
ejemplo con chrome y procesos:
- browser
- render
- plug-in

### Hay ejercicio de C y fork()

# Interprocess Comunication
Los procesos de un SO pueden ser independientes o cooperativos, estos pueden afectar o ser afectados por otros procesos o intercambio de datos.

Razones para que colaboren:
- intercambio de informacion
- mejora computacional
- modularidad
- conveniencia
### Los procesos coperativos necesitan IPC
- Shared memory :
	- muy rapdio por acceso a memoria, pero se debe coordinar la sincronizacion ej a escribe memoria y b lee memoria 
- message queue:
	- los procesos se envian msj mediante una cola de msj , es mas seguro y facil de controlar. NO comparten memoria

### IPC paso de mensajes:
los procesos se comunican y sincronizan, los msj varian de de tamaño.
se envian msj con la communication link (enlace), no solo una recibe msj o contesta necesariamente.

#### Comunicacion directa
send (p ,message) - envia un msj al proceso q
receive (q, message) - recibe un msj del proceso Q 

#### Comunicacion indirecta 
los procesos se comunican si comparten puertos:
- cada port tiene una identificacion unica
- los procesos solo se comunican con port
#### Buffering
cola de msj o buffer se implementa con:
- zero capacity: no hay msj en cola el reminente espera
- bounded capacity: longitud finita de msj
- unbounded capacity: longitud infitia

# Practica de procesos en moodle, fork y bash

