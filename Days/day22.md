
# Containers y plataforma de Docker
#
#



## Índice
### 1. Containers
### 2. Plataforma de Docker



● Aplicaciones construidas e implementadas tradicionalmente en sistemas físicos con relación 1:1.

● Las nuevas aplicaciones a menudo requieren nuevos sistemas físicos para el aislamiento de recursos.

Entornos físicos

Entornos virtuales

● Mejor utilización e implementación de aplicaciones, más rápidas que en un entorno físico tradicional.

● Las aplicaciones implementadas en máquinas virtuales son muy compatibles.



● Aceleran aún más la implementación de la aplicación.

● Reducen el esfuerzo para implementar aplicaciones.

● Optimizan el desarrollo y las pruebas.

● Menores costos asociados con la implementación de aplicaciones.

● Incrementan la consolidación de servidores.


ZZZZ

***Docker Engine, también conocido como Docker daemon***

Es el programa que permite construir, enviar y ejecutar contenedores. Utiliza espacios de nombres y grupos de control del kernel de Linux para proporcionar un entorno de tiempo de ejecución aislado para cada aplicación.

***Docker Hub*** 

Es un registro en línea de imágenes de Docker.

#
# Plataforma de Docker

***Docker Trusted Registry*** es un registro privado en el sitio para imágenes de Docker.

![Screenshot_30](https://user-images.githubusercontent.com/96561825/173213647-81c41a30-880f-4918-bdda-500299de4d55.png)



***Docker Client*** es el que toma las entradas del usuario y las envía al daemon. El cliente y el daemon pueden ejecutarse en el mismo host o en diferentes hosts.

***Docker Images*** es una plantilla de solo lectura utilizada para crear contenedores.  Contiene un conjunto de instrucciones para crear los contenedores.

Por último, ***Docker Containers*** es una plataforma de aplicación aislada basada en una o más imágenes que contiene todo lo necesario para ejecutar una aplicación.








#
#
#
#
#


See you on [Day23](day23.md)
