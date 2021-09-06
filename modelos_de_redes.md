# Modelos de Redes

## Servicios WAN punto a punto

* Comunicación por módem tradicional
* DSL/ADSL
* Comunicación por módem de cable
* Portadoras E/T
* Protocolo punto a punto (PPP)
* Red Digital de Servicios Integrados (ISDN)
* Frame Relay
* ATM
* Sonet/SDH
* DWDM 

## Bibliografía

* Transmisión de datos y redes de computadoras, Forouzan 
* Libros de CISCO (Para las prácticas) 

## Evaluación 

* Exámenes parciales (20%)
* Tareas y prácticas (20%)
* Proyecto (30%)
* Examen ordinario (30%) 

## Protocolos de enrutamiento 
* RIP
* EIGRP
* OSPF

## Customer Premises Equipment

Se refierew a teléfonos, routers, switches, etc. provistos por el proovedor de
servicios. Conecta al suscriptor con el servicio.

## ¿Qué es un baudio?

Cantidad de veces que cambia el estado de una red en un periodo de tiempo.

__NAS:__ Network Access Server 
__RAS:__ Remote Access Server

## LAN vs. WAN

Las LAN y WAN pertenecen a la capa 1 y 2.

* __Capa 1:__ Capa física
* __Capa 2:__ Capa de enlace de datos.

Una interpretación para diferenciar una de otra es la siguiente: dentro de una
LAN, es un único dueño de la infraestructura física sin importar la distancia
física.

## Definición de internet

Conjunto descentralizado de redes de comunicación interconectadas.

## PPP (Point to Point Protocol)

A finales de los 80 el protocolo SLIP presentaba una limitación al crecimiento
del internet. PPP se crea para solucionar problemas de conectividad remota de
internet. PPP era necesario para poder asignar IP's de forma dinámica y permitir
el uso de múltiples protocolos.

### Funciones PPP

* Control de la configuración del enlace de datos.
* Proporciona asignación dinámica de IP's
* Detección de errores.
* Opciones de negociación.

### Campos de la trama PPP

* Señalador (1 byte)
* Dirección (1 byte)
* Control (1 byte)
* Protocolo  (2 bytes)
* Datos  (Variable)
* FCS (2 o 4 bytes)
