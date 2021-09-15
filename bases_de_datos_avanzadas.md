# Bases de datos avanzadas

Ing. Victor Sarabia Ortiz

## Escala

* Examen teórico 40%
* Tareas 60%

__Objetivo de un respaldo:__ tener un medio de recuperación en caso de fallo.

## Instalación de VM

usuario: oracle 
password: oracle1 


__Opciones de instalación:__ (librerías de compatibilidad, development tools,
gui) 

## ¿Qué es un data warehouse?

Es un sistema que agrega y combina información de diferentes fuentes en un
almacén de datos único y centralizado. 

### Aplicaciones

* Respaldos
* Minería de datos
* Machine learning (IA)
* Análisis 

Usualmente contienen grandes cantidades de datos históricos para tener una
"única fuente de verdad" en una organización.

## Archivos que componen una BD

__Pregunta de exámen:__ ¿De qué está hecha una B.D? 

1. Data files: \*.dbf
2. Control files: Almacenan la sincronía de la B.D
3. Redo log files: registro cambio a los datos de la BD
4. Otros

```bash
# Para abrir el puerto TCP del lado del servidor
$ lsnrctl start
```
```sql
/*  Crear un archivo de parámetros en ascii (PFILE) a partir
    de uno binario (SPFILE)*/
CREATE PFILE FROM SPFILE
```
## Archivos de parámetros de inicialización

* `spfile.ora`: archivo binario 
* `initorcl.orcl`: archivo ascii

### Ejemplos de parámetros de inicialización 

* `MEMORY_MAX_TARGET`: Máxima memoria asignable.
* `PGA_AGGREGATE_TARGET`
* `SGA_TARGET` 

`SGA + PGA < MEMORY_MAX_TARGET` en donde:

* PGA: memoria usada por los clientes
* SGA: memoria usada por las instancias

__Bloque de BD:__ Unidad mínima de manipulación de datos.

```sql
SHOW PARAMETER BLOCK
```
## Diccionario de datos

El diccionario de datos se utiliza cuando se compila una instrucción.

## ¿Qué es un commit?

Un commit es el predicado que finaliza todos los cambios especificados en una transacción.
Una transacción, a su vez, es una secuencia de predicados SQL que se tratan como
una unidad.

## Espacios de memoria en la instancia en una Single Instance Database

## Shared Pool

Almacena sentencias SQL y código PSQL (cursor). Un cursor es un espacio en
memoria que almacena texto, código SQL y plan de ejecución de sentencias.

### Keep buffer cache
Una extensión del buffer cache para almacenar los bloques de datos de la BD más
frecuentemente usados.

### Recycle buffer cache

Una extensión del buffer cache para almacenar bloques de datos de la BD
esporádicamente usados después de un commit. 

### Database buffer cache

El espacio Database Buffer cache se
administra por un algoritmo llamado LRU (Less Recent Use).

### Redo log cache 

Almacena los cambios a bases de datos antes de guardarlos en un redo log file.

Campos del buffer: 

* DF 
* Bloque
* Posición 
* Valor anterior 
* Valor nuevo 
* Quién
* Timestamp
* SCN

### Java pool

Un espacio en la SGA para la JVM y para ejecutar código JAVA

### Streams pool 

Un espacio de la SGA para replicación de datos.

### Large pool

Un espacio  de la SGA para el procesamiento masivo de datos como: Buffer de IO
para respaldo y recuperación, procesos en paralelos, procesos compartidos.

## Características de los demonios (daemons)

* Especializados
* Invisibles 
* Esperando ser invocados
* Siempre corriendo

__¿Qué evento hace que un redo log file se vaya a un archive log file?__ 
    R: Log switch


```bash
# utilería de recuperación
rman target /
```

## ADDM

Módulo para monitorear y diagnosticar la B.D 

## AWR

Repositorio de cargas de trabajo de la B.D

## Método para activar el modo `archivelog`

```sql
ARCHIVE LOG LIST;
SHUTDOWN IMMEDIATE;
STARTUP mount;
ALTER DATABASE archivelog;
ALTER DATABASE open;
```
## Crear un usuario en la BD
```sql
CREATE USER carlos IDENTIFIED BY "oracle1"
ACCOUNT UNLOCK DEFAULT TABLESPACE USERS
QUOTA 10M ON USERS;

GRANT CONNECT TO carlos;
GRANT CREATE SESSION TO carlos;
```
