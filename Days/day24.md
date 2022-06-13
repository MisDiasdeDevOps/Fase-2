
# Ejercicio Docker


#
#


## Objetivos

En el siguiente ejercicio vamos a comparar la arquitectura de Docker vista previamente (Clase de Docker ) con el funcionamiento de un restaurante.

### ¿Qué recibimos?

Un Jamboard ilustrando el funcionamiento de Docker y el restaurante, de forma desordenada y el comando para ejecutar nuestro primer contenedor, el cual es un servidor web modificado:


![Screenshot_36](https://user-images.githubusercontent.com/96561825/173250150-4e87a80e-115f-48e8-b18d-61dbc68bae23.png)

docker container run -d --name spaghettidocker -p 80:80 davidpigna/spaghettidocker

#

# Instrucciones

## Ejercicio 1 

Debatir con la mesa de trabajo qué elementos de ambas estructuras son similares y reordenar la arquitectura de Docker para que coincidan en su funcionamiento.


***Tip:*** Imaginate qué es lo primero que harías al entrar al restaurante. Seguramente empezaremos pidiendo la carta, ¿qué componente de la arquitectura de Docker coincide con ese elemento del restaurante?



#
#
# Ejercicio 2


Ahora que entendemos mejor el funcionamiento de la arquitectura de Docker, ¡vamos a ejecutar nuestro primer contenedor! Con este objetivo, vamos a utilizar la herramienta Play with Docker. Esta es una máquina virtual de Alpine Linux que ejecutamos en nuestro navegador: https://labs.play-with-docker.com. Una vez registrados en el sitio, vamos a hacer clic en el botón “Start”.

![Screenshot_37](https://user-images.githubusercontent.com/96561825/173250166-ff744121-8ecb-4c76-9724-a285562eba31.png)

Una vez dentro, deberemos crear una instancia nueva:

![Screenshot_39](https://user-images.githubusercontent.com/96561825/173250175-be11a150-d8a2-405e-91e6-7e570e8b9dcf.png)



#
Aparecerá una línea de comandos en la cual ejecutaremos nuestro primer container:

![Screenshot_40](https://user-images.githubusercontent.com/96561825/173250186-fa55504d-bf88-4d28-a645-d6da93342d0e.png)

#
#
***Tip:*** Esto es lo que realizó nuestro comando:


- ***docker container run:*** le estamos diciendo al Daemon que ejecute un contenedor.

- ***d o --detach:*** ejecuta nuestro container en segundo plano.

- ***--name:***  le damos un nombre al container, de lo contrario le asignará un nombre aleatorio.

- ***-p o --publish:*** mapea los puertos del host al puerto del container.

- ***davidpigna/spaghettidocker:*** es la dirección en la cual se encuentra este container en Docker Hub (Registry).

#
#


Una vez finalizado, vamos a abrir el puerto de nuestro container para ver el servidor web que instalamos:

![Screenshot_41](https://user-images.githubusercontent.com/96561825/173250211-05d1226b-cb67-44d1-9cfc-1bf46d16be93.png)
#



Si ves la siguiente pantalla, ¡felicidades!, completaste el ejercicio.


![Screenshot_42](https://user-images.githubusercontent.com/96561825/173250222-291c280a-2983-487f-9912-c697ed4530e8.png)

#
#
#
#
#

Seguimos en el [Día 25](day25.md)
