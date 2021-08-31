# Sistemas Operativos

__alias:__ dulce 

* __Buffer de traducción:__ Ejecuta instrucciones binarias en la computadora
(circuito electrónico). 
* __Sistema Operativo:__ Conjunto de programas que administran los recursos de una
computadora. 

## Conceptos de multiprogramación 

* __CPU:__ Hardware que ejecuta instrucciones. 
* __Procesador:__ Chip físico que contiene uno o más CPU
* __Core:__ Unidad básica de cómputo de una CPU. 

__Programa boostrap:__ Primer programa que carga una computadora. Se usa para
cargar el bootloader e inicializar registros. 

## Interrupciones 

Señal eléctrica que manda el HW al CPU usualmente a través del bus del sistema. 
Cuando el CPU es interrumpido, detiene lo que hace y transfiere la ejecución
a una ubicación predeterminada en el __vector de interrupciones__. Suspende su
ejecución, guarda el stack frame, procesa la interrupción y regresa.

### ¿Cómo se realiza una interrupción? 

Un controlador de dispositivo crea una interrupción al mandar una señal a la
línea de solicitud de interrupciones. El CPU recibe la señal y despacha al
manejador de interrupciones.


## Proceso de arranque de una computadora 

1. Dirección fija apunta a EPROM. 
2. Revisión rápida de HW.
3. Busca el sector 0 del disco. 
4. Lee el programa del sector 0 y lo carga en RAM.
5. El HW cede el control, poniendo el valor adecuado en el IP y comienza el
   ciclo Von Neumann (fetch/ejecución). 
6. Comienza a leer más sectores del disp. de almacenamiento hacia la RAM (carga
   del SO).

## ¿Qué es un proceso? 

En esencia, un proceso es un programa en ejecución. Cada proceso tiene asociado
un __espacio de direcciones__. También tiene:

* Registros
* Lista de archivos abiertos
* Alarmas pendientes 
* Procesos relacionados

