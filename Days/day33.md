

# Certificados en la práctica

#
#

En el siguiente ejercicio vamos a hacer uso de la criptografía viendo cómo funciona un certificado. Para ello, vamos a ir a nuestra VPC de AWS, generaremos un dominio propio en www.noip.com y seguiremos este tutorial paso a paso que contiene todo lo que vamos a necesitar para completar el ejercicio.



Instrucciones
Creación de la instancia EC2 en la VPC.
Generación del dominio en noip.
Generación del certificado SSL en Let's Encrypt.


Creación de la instancia EC2 en la VPC
Acceso a la consola de gestión AWS
Una vez logueados en la consola de Amazon Educate, seleccionamos la opción AWS Account. Allí aparecerá listada la materia y hacemos clic en Go to Classroom.


zzzzzzzzz


Crear una instancia en EC2



pantalla y hacemos clic en el botón Launch instances. 

zzzzzzzzzzz


Seleccionamos el modelo de máquina Family T2.micro (capa free) 

zzzzzzzzzzz



En la interfaz, el Step 3 lo dejamos tal cual está y apretamos Next. En el Step 4, dejamos los discos por defecto de 8 GB, volvemos a presionar Next. En el Step 5, hacemos lo mismo. Mientras que en el Step 6 vamos a configurar, por ahora, un grupo de seguridad para el acceso a la instancia.



zzzzzz

Lo importante es darle un nombre y una descripción que nos ayude a identificarlo y dar acceso a los protocolos.

z

Hacemos clic en Review and Launch.

Corroboramos la configuración de la instancia y hacemos clic en Launch instances.


zzzzzzz

Creamos un nuevo key pair, si no tenemos, y descargamos el archivo .pem.


zzzzzzzzzzz




#
#
# Instalar Apache


Para este apartado vamos a necesitar una consola o terminal Bash para comunicarnos vía SSH. En la actualidad, hay muchos productos disponibles y depende del sistema operativo que estemos utilizando. Por el momento, dejamos a tu criterio cuál te parece más cómodo y agradable a la vista. En este ejemplo, utilizamos Windows 10 con Cmder. En caso de no tenerlo, se puede descargar de https://cmder.net —recomendamos bajar la versión full que es totalmente portable—. Copiamos el archivo de claves .pem en la carpeta raíz del Cmder, solo por comodidad del ejemplo. 


Abrimos la consola. En la parte inferior derecha abrimos un bash como administrador.


zzzzzzz

Vamos a buscar la IP de la “Instancia01” que está online.

zzzzzzzzz


Una vez dentro, tenemos que instalar un servidor Apache para deployar nuestro código. Con este objetivo, ponemos el siguiente comando:

zzzzzzzzzz

Comprobamos que el servicio esté andando. Ingresamos a un explorador y colocamos la IP de nuestra instancia y nos debe contestar: Apache2 recientemente instalado


zz

Luego, clonamos el repositorio del proyecto  En este caso, lo tenemos en el repositorio público de Github.


zzzz


Ingresamos nuevamente a la instancia a través del navegador web.

zzz


#
#
# Generación del dominio en noip


Ingresamos en nuestro navegador a www.noip.com.


Luego, creamos nuestro nombre de dominio propio. Vale la pena aclarar que en este punto tenemos que colocar nuestro nombre único de dominio para poder redireccionar a nuestra EC2.

Confirmamos en nuestra casilla de correo electrónico y luego vemos lo siguiente:
zzz


Iniciamos sesión en www.noip.io , luego nos dirigimos en el menú de la izquierda a DNS Dinámico y finalmente Nombre de host sin IP.

zzzzzz



Modificamos el dominio que creamos con la IP de la instancia de EC2 que creamos.


zzzzzzzz

Damos en actualizar, y ¡listo! Ya tenemos nuestro domino online. En este caso, devopsddns.net (recordá que este es el ejemplo que utilizamos para este tutorial. No podés usar este mismo dominio porque ya está ocupado)


zzzzzzz


#
#
# Generación del certificado SSL en Let’s Encrypt 
#

## Instalar Certbot

El primer paso para utilizar Let's Encrypt para obtener un certificado SSL es instalar el software Certbot en el servidor. Para ello ingresamos nuevamente a nuestra 
instancia EC2 por medio de nuestro archivo .pem en la AWS. Luego, instalamos las dependencias necesarias:


zzzzz

Comprobamos la presencia del repositorio de universe.
zzzzzzzzzzzz



Nuevamente actualizamos la lista de paquetes disponibles.
zzzzzzzzzzz




#
## Certbot para Apache

Ejecutamos este comando desde nuestra la línea de comandos para instalar Certbot:


zzzzzzzzzzzz

#
## Configuración de firewall (UFW)


Si el firewall UFW está habilitado, debemos crear una nueva regla para permitir el tráfico HTTPS. Para verificar si el firewall está activo, ejecutamos este comando:


zzzzzzzzzzzz

Para permitir el tráfico HTTPS para Apache:
zzzzzzzz


#
## Obtener un certificado SSL


Certbot utiliza el complemento Apache para obtener certificados SSL:
zzzzzzzzzz





Nos va a pedir un mail para registrarnos, y la configuración de los directorios que podemos responder “mail”,“y” y “a”.

zzzzzzzzzzzzzz




La ejecución de este comando permitirá obtener un certificado SSL y Certbot modificará automáticamente la configuración de Apache. De lo contrario, podríamos obtener el certificado SSL y luego configurar Apache manualmente con el siguiente comand




Ingresamos nuestro dominio, en este casodevops.ddns.net.


#
#
# Renovación automática (opcional)


Los paquetes de Certbot vienen con un trabajo Cron que renovará automáticamente sus certificados antes de que caduquen. Dado que los certificados Let's Encrypt duran 90 días, se recomienda encarecidamente aprovechar esta función. Podemos verificar la renovación automática de certificados ejecutando este comando:


zzzzzzzz


El comando para renovar Certbot se instala en una de las siguientes ubicaciones:





Para confirmar que Certbot se ha instalado correctamente, podemos visitar el sitio web configurado —https://devops.ddns.net— en el navegador y buscar el ícono de candado en la barra de URL.


#
#
## Conclusión

De esta manera hemos concluido con el tutorial para armar nuestro sitio con certificación ***Let's Encrypt.*** 


Esta nos permitirá brindar la seguridad necesaria para adjuntar información cifrada.

















 





















#
#
#
#
#

See you on [Day 34](day34.md) 
