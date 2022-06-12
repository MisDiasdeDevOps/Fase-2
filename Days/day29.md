# Docker Hub


Docker Hub es un servicio
de registro de repositorios
proporcionado por Docker
Inc. Compartir y colaborar
son sus premisas.



Índice

1. ¿Para qué sirve Docker Hub?
2. Características de Docker Hub
3. Creación del primer repositorio
4. Explorar las imágenes
5. Descargar una imagen
6. Crear una imagen
7. Empujar una imagen
8. ¿Qué son las imágenes certificadas
por Docker?
9. Imágenes populares en Docker Hub


#
## ¿Para qué sirve Docker Hub?


Nos permite extraer y enviar imágenes de la ventana
acoplable hacia y desde Docker Hub. Podemos
tratar esto como un GitHub, donde obtenemos y
enviamos nuestro código fuente, pero en el caso de
Docker Hub descargamos o publicamos nuestras
imágenes de contenedor.
Es un repositorio en línea basado en la nube que
almacena ambos tipos de repositorios, es decir, el
repositorio público y el privado. Los repositorios
públicos son accesibles para todos, pero el privado
es accesible para el propietario interesado de los
repositorios. También hay un costo asociado si
almacenamos más de un cierto número de
repositorios como privado.


#
## Características de Docker Hub



Una vez que hayas iniciado
sesión, podés crear el
repositorio haciendo clic en
“Crear repositorio” en la
página de bienvenida.
Luego, te pedirá un nombre
y le dará un nombre a tu
repositorio.

Podés seleccionar una visibilidad pública o
privada. También podés integrar tus repositorios
de código fuente como GitHub y Bitbucket a
través de la configuración de compilación, pero es
opcional (y también se puede hacer en una etapa
posterior).
Una vez que todo esté hecho, se debe hacer clic en
‘’Crear’’. Con estos pasos podés crear tus primeros
repositorios. En la próxima diapositiva podés ver
cómo se verán.


zzzzzzzzzzz


Docker Hub nos ofrece solo un
repositorio privado de forma gratuita.
Si necesitamos más repositorios privados,
podemos actualizar nuestra cuenta a un
plan pago.
Con la herramienta terminal de Docker
Desktop, descargada e instalada,
podremos iniciar sesión en Docker Hub
mediante un comando.


#
## Explorar

#

Hay dos formas de buscar imágenes y
repositorios públicos desde Docker Hub.
Podés buscarlo en el sitio web de
Docker Hub o usar la herramienta de
línea de comandos y ejecutar el
siguiente comando, suponiendo que
queremos buscar en la imagen del
repositorio de MySQL.

zzzzzzzzzzzzz




#
## Descargar una imagen

Podemos descargar una imagen de Docker Hub usando el comando pull de la
siguiente manera:


zzzzzzzzzzzzz

Si ya tenemos mysql image en nuestra máquina, el comando anterior actualizará
automáticamente la imagen a la última versión. Una cosa a tener en cuenta aquí es
que si notamos la salida del comando de búsqueda de la ventana acoplable, hay
muchas imágenes de MySQL en Docker Hub, y eso se debe a que cualquiera puede
enviar una imagen. Pero depende de nosotros saber cuál usar en función de nuestro
caso de uso y asegurarnos de que sea el apropiado.
Digamos que queremos extraer una imagen bitnami/mysql:

zzzzzzzzzzzzzzzzz



#
## Crear una imagen 



El proceso de crear una imagen requiere un Dockerfile. Podemos pensar un Dockerfile
como un manual de instrucciones que le dice a Docker qué ensamblar. En resumen,
es un archivo de configuración que sigue ensamblando instrucciones.


¿Cómo funciona?


Docker lee las instrucciones de un Dockerfile y crea imágenes automáticamente. La
imagen de Docker es un sistema de archivos en capas y consta de varias capas de solo
lectura. Cada capa de una imagen de Docker representa las instrucciones de un
Dockerfile. A continuación, sigamos los pasos para crear una imagen usando un


zzzzzzzzzzzzzzz


Nota: el nombre del archivo debe ser Dockerfile con “D” mayúscula.


zzzzzzzz

Echemos un vistazo a algunas de las palabras clave importantes que se utilizan en Dockerfile. Podemos utilizar # para agregar un comentario en un Dockerfile.



FROM (de): define la imagen base que se utilizará.
MANTEINER (mantenedores): persona que va a mantener esa imagen.
RUN (correr): se utiliza para ejecutar la instrucción dada para la imagen. En nuestro
caso, primero actualiza el sistema y luego instala MySQL.
CMD: se utiliza para ejecutar un comando una vez que se ha lanzado el contenedor.
COPY (copiar): se utiliza para copiar un archivo de nuestro sistema operativo host al
contenedor de la ventana acoplable.
EXPOSE (exponer): se utiliza para especificar el número de puerto en el que el
contenedor ejecutará su proceso.



Una vez que nuestro Dockerfile se ha creado correctamente, debemos ejecutar
docker build para “armar” nuestra imagen localmente, para luego enviarla a Docker
Hub. Este comando debemos ejecutarlo dentro de la carpeta donde se encuentra el
Dockerfile.



zzzzzzzzzzz


Podemos verificar que la imagen está creada con la siguiente línea de código:



zzzzzzzzzzzzzzzzzzzzzz




#
## Empujar una imagen

Una vez que nuestra imagen se ha creado correctamente y se está ejecutando, podemos enviarla a Docker Hub mediante el comando push.

zzzzzzzzzzzzzz

Podemos verificar las etiquetas de la imagen y el estado en Docker Hub, que se verá así.


zzzzzzzzzzzzzz


#
# ¿Qué son las imágenes certificadas por Docker?


Estas son las imágenes oficiales impulsadas por
proveedores o contribuyentes. Una imagen solo
puede ser certificada por Docker Hub si su contenido
cumple con las reglas, estándares y leyes
proporcionadas por Docker Hub. En resumen, esa
imagen debe pasar ciertas pruebas de referencia.
Docker Hub proporciona inspectDockerImage,
herramienta a través de la cual un proveedor puede
autocertificar las imágenes y los complementos (por
lo general, el proveedor o contribuyente publica sus
complementos para registrar volúmenes y redes).

#
## Imágenes populares



Imágenes populares en Docker Hub


Hay muchas imágenes seleccionadas y
optimizadas disponibles en Docker Hub. La
popularidad de estas imágenes depende de
varios factores, presencia en el mercado,
calificaciones, puntajes de satisfacción,
entre otros. Para obtener una lista detallada
de los repositorios más populares, podés
visitar el sitio web de Docker Hub. El uso de
una imagen también depende del sistema
operativo y su arquitectura.


Si conocemos para qué sistema operativo y
arquitectura se utilizarán las imágenes,
debemos considerar los siguientes factores
clave antes de extraer una imagen:
● Buscar una versión específica utilizando
etiquetas (principalmente la última).
● Optar por el que tenga máxima cantidad
descargas y estrellas.
● Buscar la fecha de su última
actualización.
● Si es posible, verificar su tipo, ya sea del
editor verificado u oficial (Docker
Certified).


































fin

#
#
#
#
#





See you on [Day 30](day30.md)
