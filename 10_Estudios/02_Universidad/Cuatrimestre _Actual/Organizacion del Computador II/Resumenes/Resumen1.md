# RISC vs CISC

## Dos formas de diseñar una micro-arquitectura
### RISC

utiliza instrucciones simples y rapidas que se ejecutan en un solo ciclo, es mas eficiente energeticamente.Utiliza mas registros. menos modos direcionamiento mayor complejidad en el compilador.Sacrifica cantidad de instrucciones para reducir la complejidad y cantidad de instrucciones-
- intrucciones menos complejas
- De proposito general
- Codigo mas largo
- Compiladores mas complejos
- Mas ciclos por tarea
- opera solo sobre registros en gran cantidad
- Diseño de circuitos menos complejo
- Instrucciones de igual tamaño

Intrucciones de maquin --> Ejecucion de instrucciones

Arquitecturas: ARM-MIPS-ATMEL

### CISC
Emplea instrucciones complejas que realizan multiples oraciones por instruccion, optimizanco el tamaño del codigo.Posee menos registros pero mas modos de direccionamiento, utiliza micropragramacion

Intrucciones de maquina --> Conversion a microcode --> Microinstrucciones --> Ejecucion Microinstrucciones

- Instrucciones mas complejas de varios ciclos de clock y especificas
- Instrucciones poco optimizadas
- Compiladores mas sencillos y codigo mas reducido
- menos ciclos por tarea
- Puede acceder directamente a memoria
- Mayor complejidad de circuitos
- Distinto tamaño de instrucciones

Arquitecturas: Intel x86-AMD x86-64

# Sistemas de Buses

- Bus de datos:Transporta informacion
- Bus de control: Indica la ubicacion de memoria o del dispositivo con el que se desea comunicar
- Bus de direccion: Gestiona la sincronizacion y el sentido de la transferencia (lectura/escritura)
### Cuello de Botella de Von Neumann

- Prefetch (búsqueda anticipada) de instrucciones: consiste en que el procesador busca instrucciones en memoria antes de que sean necesarias para su ejecución, almacenándolas temporalmente en un buffer interno. 
- Memoria caché: es una memoria pequeña, muy rápida, ubicada entre la CPU y la memoria principal. Su función es almacenar temporalmente los datos e instrucciones más utilizados. 
- Pipeline de instrucciones (paralelismo a nivel de instrucción): es una técnica que permite ejecutar varias instrucciones simultáneamente en distintas etapas de procesamiento.La ejecucion de instrucciones se divide en etapas independientes que  pueden operar en paralelo con distintas instrucciones,aumentando la cantidad de instrucciones inicidadas por unidad de tiempo.

# Evolucion de microprocesadores intel
Etapas:
	- Arquitectura de 16bits (8086 - 80286)
	- Arquitectura de 32bits (IA-32)
	- Arquitectura de 64bits (x86-64)
Evolucion de los microprocesadores:
	- intel 8086  y 8088
	- intel 80186
	- intel 80286
	- intel 80386 (IA-32)
	- Pentium
	- Pentium Pro/2/3
	- Intel core de cuarta generacion

## Intel 8086/8088
Primer procesador de la famila x86.El intel 8088 fue adopatado para las pc,la diferencia entre ambos radica en el bus de datos de 8086 maneja 16bits y el 8088 maneja 8bits.
- Arquitectura 16bits
- Bus de direcciones 20 bits
- Memoria direccionable 1 MB
- Frecuencia 6-12Mhz
## Intel 80186
El Intel 80186 introducido en 1982 fue diseñado como una version mejorada del 8086, manteniendo su compatibilidad con el conjunto de instrucciones.
- Arquitectura 16bits
- Bus de direcciones 20 bits
- Memoria direccionable 1 MB
- Frecuencia 6-12Mhz
## Intel 80286
El Intel 80286 tuvo un salto de arquitectura significativo, fue pensado para SO multitarea y proteccion de memoria.
- Arquitectura 16bits
- Bus de direcciones 24 bits
- Memoria direccionable 16MB
- Frecuencia hasta 25 Mhz

### Modo Protegido
Permite implementar caracteristicas fundamentales para sistemas operativos multitarea
- proteccion de memoria
- aislamiento de procesos
- control de acceso a recursos
- gestion segura de programas concurrentes
Un programa no puede acceder libremente a toda la memoria del sistema, sino unicamente a la memoria asignada por el sistema

### Descriptores de segmento
En el modo protegido los segmentos dejaron de ser simples valores en registros y pasaron a estar definidos en descriptores de segmento almacenados en tablas especiales.
Cada descriptor puede contener:
- direccion base del segmento
- tamaño del segmento
- tipo de segmento
- privilegios de acceso
### Tablas de descriptores
Global Descriptor Table (GDT):contiene descriptores accesibles para todo el sistema.
Local Descriptor Table(LDT) contiene descriptores especificos de un proceso.
Esto permite aislar programas entre si.

## Intel 80386
introdujo la arquitectura IA-32 que seria la base de los sistemas durante mas de dos decadas.
- Arquitectura 32 bits
- Bus de direcciones 32 bits
- Memoria direccionable 4 GB
- Frecuencia hasta 12-40 Mhz

Introdujo el *Modo Virtual* que permite ejecutar programas antiguos del intel 8086 dentro de un entorno protegido, garantizando compatibilidad con software existente.

### Registros Extendidos
Los registros se ampliaron de 16 a 32 bits
Registro 16 bits AX  BX  CX  DX 
Registro 32 bits EAX EBX ECX EDX

### introduccion a la paginacion
La paginacion permite dividir la memoria en bloques de tamaño fijo llamado paginas, el SO puede mapear direcciones virtuales a direcciones fisicas mediante tablas de paginas.
Permitiendo integrar la memoria virutal una caracteristica esecnial de los SO modernos.

## Intel 80486
El Intel 80486 implemeto mejoras de rendimiento como la pipeline de 5 etapas, memoria cache L1 integrada,copreocesador matematico integrado(FPU) y mayor frecuencia de reloj,
- Arquitectura 32 bits
- Bus de direcciones 32 bits
- Memoria direccionable 4 GB
- Frecuencia hasta 25-100 Mhz
## FPUx87 (Unidad de punto Flotante)
Es la unidad de calculo en punto flotante de la arquitectura IA-32,integrada desde el 80486 que opera bajo el estandar IEEE-754
con un formato interno de 80bits de precisione extendida.Se basa en una pila circular de 8 registros.Ademas su entorno se compone de registros de estado,control,etiquetas y punteros que gestionan excepciones criticas, como division por 0.overflow y underflow.
Hoy en dia fue remplazado por tecnologias mas modernas como SSE y AVX que permiten paralelismo, sigue siendo un concepto fundamental de la arquitectura x86 para sistema legacy y procesamiento numerico.
### Pipeline de instrucciones
la pipeline permite superponer la ejecucion de varias etapas,aumentando asi el rendimiento del procesador:
- Fetch
- Decode
- Execute
- Memory
- Write Back
### Memoria cache integrada
Primer procesador x86 en integrar memoria cache L1 dentro del chip, esta almacena instrucciones y datos utilizados recientemente reduciendo el tiempo de acceso a memoria.
### Coprocesador matematico integrado
En procesadores anteriores el calculo de punto flotante era realizado por un coprocesador externo, el intel 80486 integro una FPU dentro del chip mejorando el rendimiento en apps cientificas y de ingenieria.

## Intel Pentium
Introdujo el concepto de arquitectura superescalar, tiene dos pipelines de ejecucion y un bus de datos de 64bits.
- Arquitectura 32 bits
- Bus de direcciones 32 bits
- Memoria direccionable 4 GB
- Frecuencia hasta 60-200 Mhz
### Ejecucion paralela
En anteriores procesadores se ejecutaba una instruccion por ciclo de reloj, la arquitectura superescalar permite ejecutar multiples instrucciones simultaneamente,logrando multples unidades de ejecucion.

### Doble Pipeline
- Pipeline U(primario)Ejecuta cualquier instruccion tanto simples como complejas.
- Pipeline V (secundario)Ejecuta unicamente instrucciones simples enteros(de uso frecuente)
### Bus de datos de 64bits
El pentium amplio el bus de datos externo a 64bits duplicando la cantidad de datos transferidos por ciclo, mejorando el acceso a memoria.

### Ejecucion fuera de orden
En arquitecturas tradicionales las instruccions se ejecutan estrictamente en el orden que aparecen los programas.Sin embargo, esto puede generar bloqueos en el pipeline cuando una instruccion depende del resultado de otra.
La ejecucion fuera de orden permite:
- reorganizar instrucciones
- ejecutar primero aquellas que no tiene dependencias
- maximizar el uso de las unidades de ejecucion

### Ejecucion especulativa
Consiste en predecir el resultado de una instruccion de salto y continuar ejecutando instrucciones posteriores antes de conocer el resultado real.
- Si la predicciones es correcta: se gana tiempo de ejecucion.
- Si la predicciones es incorrecta:se descartan los resultados y se reanuda la ejecucion correcta.

El CPU intenta predecir el futuro para mejorar el rendimiento, en caso que el CPU sepa que un programa tenga multiples ramas logicas, calcula sus resultados antes de saber cual ejecutar.
Si A=True --> Calcular X
Si A=False --> Calcular Z

Calcularia X y Z antes de saber el valor de A, otro tipo de ejecucion especulativa es aprovechar el tiempo ocioso de CPU para calcular una instruccion pedida a menudo.
### Renombrado de registros
Esto evita conflictos artificiales cuando distintas instrucciones utilizan el mismo registro logico.
El procesador asigna registros fisicos diferentes,permitiendo mayor paralelismo.

## Intel pentium Pro 
Introdujo tecnologias fundamentales como la ejecucion fuera de orden,especulativa y el renombrado de registros.
- Arquitectura 32 bits
- Bus de direcciones 36 bits
- Memoria direccionable 4 GB
- Frecuencia hasta 150-200 Mhz
### Intel pentium II
Incorpora mejoras de rendimiento y extensiones multimedia con Multimedia Extensions (MMX)
- Arquitectura 32 bits
- Bus de direcciones 36 bits
- Memoria direccionable 4 GB
- Frecuencia hasta 233-450 Mhz
### Intel pentium III
El intel pentium III incorpora Streaming SIMD(Single instruccionm, multiple data) Extension
- Arquitectura 32 bits
- Bus de direcciones 36 bits
- Memoria direccionable 4 GB
- Frecuencia hasta 233-450 Mhz

### Arquitectura X86-64
La arquitectura moderna x86-64 amplia los registros a 64bits
Caracteristicas:
- Multiples nucleos
- Ejecucion fuera de orden avanzada
- Cache multinivel
- soporte para virtualizacion
- Extensiones vectoriales

### Ampliacion del espacio de direcciones
En arquitecturas de 32bits: 232 = 4gb
Esto resulto insuficiente para aplicaciones modernas.
La arquitectura moderna amplia el espacio teorico de 264

### Arquitectura multinucleo
Los procesadores moderno incluyen multiples nucleos de procesamiento,permitiendo ejecutar varios hilos en simultaneo.
Mejora el rendimiento en:Servidores-Aplicaciones cientificas-Procesamiento paralelo.

### Jerarquia de memoria cache
Existen multiples niveles en procesadores modernos:
- CacheL1
- CacheL2
- CacheL3

### Modos de Operacion IA-32
Pueden operar en distintos modos
- Modo real: Corresponde al funcionamiento original del 8086
- Modo protegido: Introducido con el 80286
- Modo Sistema: En arquitecturas modernas se incluye un modo sistema o supervisor, utilizado por el SO para ejecutar operaciones privilegiadas.

### Modo Real
Caracteristicas:
- Direccionamietno de 20 bits
- Maximo 1 MB de memoria
- Sin proteccion de memoria
- Acceso directo a hardware

Este modo se utiliza durante el arranque o reincio del sistema.

### Modo Protegido
Es el modo nativo del procesador. Puede ejecutar directamente codigo de modo real en un ambiente protegido y multitarea.
Caracteristicas:
- Acceso a memoria extendida
- Proteccion entre procesos
- Niveles de privilegio
- Soporte multitarea
Se definen cuatro anillos de privilegio:
- Ring 0: Kernel
- Ring 1: Servicios del sistema
- Ring 2: Drivers
- Ring 3: Aplicaciones

### System Management Mode
En arquitecturas modernas se incluye un modo de surpervisor o sistema ,utilizado por el sistema operativo para ejecutar operaciones privilegiadas.
Este modo permite:
- Manejo de memoria
- control de dispositivos
- Gestion de interrupciones

### Pipeline escalar
- Permite la ejecucion solapada de instrucciones
- Analogo a linea de montaje de una fabrica

1 Fetch | Decode | Execute
	2 Fetch | Decode | Execute
		3 Fetch | Decode | Execute
### Hyper Threading
- Simula tener mas nucleos para el SO
- 2 hilos (threads) por nucleo
- Aprovecha las unidades de ejecucion ociosas
- Mejora la performance sin aumentar mucho el consumo

Por ejemplo de 4 nucleos fisicos se obtienen 8 en total con hyper threading 

## Gestion de Memoria

### Espacio Fisico
IA-32 organiza la memoria como una secuencia de bytes, este se direcciona a travez de su bus de direccciones.
la memoria conectada se la denomina como memoria fisica y se denominan direcciones fisicas al espacio de direcciones que pueden volcarse sobre el bus.
### Espacio logico
El espacio de direcciones fue organizado en segmentos.
- 4 registros de segmento para almacenar hasta 4 selectores de segmento
- Registros de 16bits los segmentos tienen a lo sumo 64k de tamaño
- Expresion de las direcciones en el modelo de programacion mediante dos valores:
	- identificador del segmento en el que se encuentra la variable o la instruccion que se desea direccionar
	- Desplazamiento,offset,o direccion efectiva a partir del inicio de ese segmento en donde se encuentra efectivamente.

Una direccion de memoria experesad en termino de los recursos de la arquitectura del procesador la llamaremos direcion logica.
*Id.Segmento:Offset*
Estos dos valores por si solosno tienen significado fisico.
para lograr a partir de ellos identificar la direccion fisica o la variable o instruccion el procesador debe realizar operaciones

## Modo de Operacion
- Modo protegido: es el estado nativo del procesador, tiene capacidad de ejecutar directamente el software 8086 en un entorno protegido y de multitarea.
- Modo Real: implementa el entorno del 8086 con extensiones, el procesador se coloca en modo direccion real despues del encendido o reinicio
- System management mode(SMM) proporciona mecanismos para implementar funciones especificas sobre la plataforma, como la administracion de energio o seguridad.
- Modo compatibilidad: permite la mayoria de las versiones anteriores de 16bits y las aplicaciones de 32bits se ejecutan sin volver a compliar en un SO de 64bits.
- Modo de 64bits: permite que un SO de 64bits ejecute aplicaciones funciones escritas para acceder al espacio de direcciones lineales de 64bits 
### Modelos de memoria
- Flat model: la memoria aparece para un programa como un espacio de direcciones unico y continuo, llamado espacio de direcciones lineal, el codigo,datos y las pilas estan contenidos en este espacio de direcciones.
- Real Model: utiliza una implementacion especifica de memoria segmentada en la que el espacio de direcciones lineal para el programa y el SO consta de una serie de segmentos de hasta 64kb de tamaño cada uno.
- Segmented Memory: la memoria aparece para un programa como un grupo de espacios de direcciones independientes llamados segmento. El codigo lso datos y el stack suelen estar contenido en segmentos separados . Para leer un byte en un segmento, un programa emita una direccion logica, un selector de segmento y un desplazamiento. El selector de segmento identifica el segmento al que se debe acceder y el desplazamiento identifica yun byte en el espacio de direcciones del segmento
### GDT y LDT
Cada sistema debe tener un GDT definida que puede usarse para todos los programas y tareas en el sistema, opcionalmente se pueden definir uno o mas LDT. La GDT es una estructura de datos en un espacio de direcciones lineal, la direccion lineal y el limite de GDT debe cargarse en el registro GDTR.
La GDT debe contener un descriptor de segmento LDT para el segmento, si el sistema admite multiples LDT , cada uno debe tener un selector de segmento descriptor de segmento sepadaros en la GDT
la direccion lineal base, el limte y los derechos de accso de LDT se almacenan en el registro LDTR