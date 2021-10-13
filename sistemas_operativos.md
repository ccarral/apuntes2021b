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

## Llamada a sistema `fork()`

Cuando se hace la llamada a sistema `fork`, ésta devuelve el PID del nuevo
proceso (el proceso hijo) en el proceso padre y `0` en el proceso hijo. 

De acuerdo a `man fork`:
```man
FORK(2)                                                            Manual del Programador de Linux                                                            FORK(2)

NOMBRE
       fork - crean un proceso hijo

SINOPSIS
       #include <sys/types.h>
       #include <unistd.h>

       pid_t fork(void);

DESCRIPCIÓN
       fork  crea  un proceso hijo que difiere de su proceso padre sólo en su PID y PPID, y en el hecho de que el uso de recursos esté asignado a 0.  Los candados de
       fichero (file locks) y las señales pendientes no se heredan.

       En linux, fork está implementado usando páginas de copia-en-escritura (copy-on-write), así que la única penalización en que incurre fork es  en  el  tiempo  y
       memoria requeridos para duplicar las tablas de páginas del padre, y para crear una única estructura de tarea (task structure) para el hijo.

VALOR DEVUELTO
       En  caso  de  éxito, se devuelve el PID del proceso hijo en el hilo de ejecución de su padre, y se devuelve un 0  en el hilo de ejecución del hijo. En caso de
       fallo, se devolverá un -1 en el contexto del padre, no se creará ningún proceso hijo, y se pondrá en errno un valor apropiado.

ERRORES
       EAGAIN fork no puede reservar sufficiente memoria para copiar las tablas de páginas del padre y alojar una estructura de tarea para el hijo.

       ENOMEM fork no pudo obtener las necesarias estructuras del núcleo porque la cantidad de memoria era escasa.

```

## Interrupciones

Tipos de interrupciones:

* Interrupciones por software
* Interrupciones por hardware

__quantum:__ Longitud de tiempo que se le asigna a cada programa para ejecutarse
en un entorno multiprogramación


## Hilos vs. Procesos

En comparación con los procesos, los hilos son manejados desde un mismo proceso.
Comparten el mismo espacio de direcciones dentro del mismo proceso y son más
fáciles de crear y destruir.

## Regiónes críticas

Son las regiones de memoria que pueden ser modificadas por múltiples procesos.

## Condiciones de carrera

Ocurren cuando dos procesos quieren escribir/leer un recurso compartido
simultáneamente y el resultado final depende directamente del orden en el que
las operaciones de e/s fueron registradas.
