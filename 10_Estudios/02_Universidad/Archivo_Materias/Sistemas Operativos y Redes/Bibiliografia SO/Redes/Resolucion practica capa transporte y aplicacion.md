### Ejercicio 0:
a) Que es una conexión en la capa de transporte?

b) Que es un puerto? Un puerto es un número lógico utilizado para identificar aplicaciones o servicios dentro de un dispositivo. Permite que múltiples aplicaciones puedan comunicarse simultáneamente utilizando la red.
Un puerto es un process id. Un número de 16 bits, utilizado para identificar protocolo de capa superior que el SO asigna en tiempo de ejecución.

### Ejercicio 1:
a) Cual es la principal función de la capa Transporte?
### Ejercicio 2 (V o F)
a) Un Protocolo es sólo un conjunto de servicios ofrecidos para comunicar información de un lugar a otro. 
b) El Protocolo UDP se encuentra ubicado dentro de la capa de enlace. 
c) El orden en que es empaquetada la información durante la encapsulación de protocolos en el modelo OSI es: Paquete, Datos, Segmento, Trama/Frames, Bits.

a) VERDADERO - Un protocolo es un conjunto de reglas, normas que permite la comunicación entre 2 dispositivos, esto da como inicia la conversación, errores y como termina. Organiza la información entre origen y destino.
b) FALSO - El protocolo UDP se encuentra ubicado dentro de la capa de transporte.
c) FALSO - El orden de empaquetado Datos → Segmento → Paquete → Trama → Bits

### Ejercicio 3:
Si el tamaño de la ventana de transmisión cambia de 3000 a 4000 durante la transferencia de datos de una sesión TCP, ¿qué puede hacer la terminal que está enviando? 

a) Transmitir 4000 bytes antes de esperar por un ack 
b) Transmitir 3000 tramas antes de esperar por un ack 
c) Transmitir 4000 segmentos antes de esperar por un ack 
d) Transmitir 4000 paquetes antes de esperar por un ack
e) Transmitir 3000 bytes antes de esperar por un ack

#### la repuesta es la A como cambia de 3mil a 4mil durante la transferencia, ese msj es de 4mil, entonces espera del receptor 4mil y recién ahi lo manda. Ventana = bytes

# Capa de Aplicación 
### Ejercicio 1 
En qué consiste el protocolo HTTP? Cómo se relaciona con el protocolo DNS? 
### Ejercicio 2 
Indique para cada uno de los protocolos enunciados, la definición que más se asemeja: 
Protocolo | Definicion
	1            UDP   -->     No orientado a la conexion
	2            ARP    -->    traduce direcciones IP a direcciones MAC
	3           DHCP  -->    Asigna direcciones IP de forma dinamica
	4            TCP     -->   Orientado a la conexion
	5            PAT     -->   Tranforma direcciones IP 
	
### Ejercicio 3(mas de parcial)
Describir detalladamente el protocolo DNS
DNS (Domain Name System) es un sistema jerárquico y distribuido que traduce nombres de 
#### dominio en direcciones IP.
- Funciona principalmente sobre UDP
- Distribución mundial
- Base de datos jerárquica (?)
#### Proceso de resolución (protocolo DNS):
1. El cliente consulta al servidor DNS local
2. Si no conoce la respuesta:
3. Consulta a un servidor raíz
4. Luego a los distintos servidores de los distintas extensiones de dominio
5. Obtiene la IP
6. Se guarda en caché para la próxima

Packet tracer version en moodle.