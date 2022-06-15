
# Desafio AWS -
# Creación de Instancia EC2 Con User Script y Creacion de Snapshot


En este desafio deberemos realizar esta actividad y entregar al tutor nuestra implementacion en un archivo zip junto con capturas de pantalla de la realizacion (Debe observarse la cuenta del alumno)

#

### Crear una instancia de EC2

#
#

## 3.1 Encuentre y elija crear una instancia EC2


Desde la consola de gestión (AWS management console) podemos visualizar distintas opciones o servicios que nos ofrece AWS. 
#

![Screenshot_5](https://user-images.githubusercontent.com/96561825/173652523-3478a95c-96bf-45e5-854c-b597d6e0cf6e.png)
#

Así que hagamos clic en el menú expandible y veamos que nos ofrece todos los servicios de AWS, ya categorizados. 

Tiene una variedad tan grande que puede ser confuso para un nuevo usuario.

Lo que nos interesa a nosotros es EC2. 
#
![Screenshot_6](https://user-images.githubusercontent.com/96561825/173652801-e0a8c05d-4871-4b3e-a593-3d98dfc145cc.png)
#


Vamos a clicar allí.
#


Ahora estamos ubicados en el panel de EC2. 
#
![Screenshot_7](https://user-images.githubusercontent.com/96561825/173653401-fc97b906-1e5d-4ea7-990b-69218bca6ba7.png)

#

Antes de ingresar al proceso de inicio de la instancia, hay otra configuración no tan obvia que debemos establecer – establecer la región donde queremos que se cree nuestra instancia. La región activa actual se encuentra en la esquina superior derecha. 

Cuando proceda a crear una instancia EC2, se ubicará físicamente en el Centro de datos de la región que haya elegido desde arriba. 

Por lo tanto, cambie la región a la deseada (en nuestro caso, París porque es la más cercana) y haga clic en «Launch Instance» como se muestra en la imagen a continuación.



#
#

## 3.2 Elegir el AMI  - AMAZON MACHINE IMAGE -
En la siguiente pantalla, debemos elegir la imagen que nos gustaría usar para nuestra instancia EC2. 

Igual, en el menú de la derecha, tenemos la opción de filtrar solo AMI de nivel libre. 

Entonces, cuando ingresamos con fines de investigación, hacemos clic en esa casilla de verificación así que solo aparecen imágenes de nivel libre. 

Después, seleccionamos la AMI de Amazon Linux.
#
![Screenshot_8](https://user-images.githubusercontent.com/96561825/173654869-e8727002-86d5-46e5-a40f-3a39c980f66b.png)
#

#
#

### Importante:
### Que elijamos usar AMI solo con el nivel gratuito no significa que estemos exentos de pagar por este servicio.
### Cada AMI tiene diferente «instance type» y algunas de ellas son de pago, otras no. 
### Podemos distinguir si un AMI es parte del nivel libre por la etiqueta que buscaremos a continuación.

#
#

El siguiente paso es elegir nuestro tipo de instancia (el AMI). 

Podemos ver que hay muchos tipos con diferentes características, para diferentes necesidades. 

A medida que avanzamos en la lista, se vuelven cada vez más caros. 

Observe de cerca el AMI preseleccionado automáticamente.

Sobre la columna de tipo de instancia, tiene una etiqueta verde que dice «Free tier eligible».

#
![Screenshot_9](https://user-images.githubusercontent.com/96561825/173656491-d2fdc4d9-022b-45bf-8339-ad7b45fe1b8e.png)

#
![Screenshot_10](https://user-images.githubusercontent.com/96561825/173671433-32bbea55-cbed-4fab-ad36-a7fe0286a48b.png)
#


## 3.3 Parar por un momento y entender el pago

La etiqueta dice: «Las micro instancias son elegibles para el nivel de uso gratuito de AWS.

Durante los primeros 12 meses posteriores a la fecha de registro de AWS, obtendrá hasta 750 horas de micro instancias cada mes. 

Cuando su nivel de uso gratuito caduca o si su uso excede las restricciones del nivel gratuito, usted paga tarifas estándar de servicio de pago por uso. 

Obtenga más información sobre la elegibilidad y restricciones del nivel de uso gratuito» 

Las siguientes dos preguntas que surgen en nuestras mentes son:

● ¿Pero cuáles son las otras limitaciones? 

En el momento en que escribo este tutorial, se le cobrará si:

- Superamos más de 750 horas de tiempo de actividad por mes o la configuración de hardware de la máquina (RAM, cpu credits, .etc).
- Los 12 meses de free plan han terminado.
- Usando un AMI que NO tiene la etiqueta que indica que es parte del plan gratuito.

- Para conocer las otras limitaciones que nos ofrece el nivel gratuito de cada servicio de AWS, le sugiero que visite el sitio web de AWS y haga clic en el menu Pricing -> AWS Free Tier.

- El precio y las limitaciones pueden cambiar para cuando lea este tutorial. 

- Por lo tanto, ingrese el enlace que he proporcionado y asegúrese de conocer los límites del servicio que está utilizando.

- ¿cómo saber el precio de un AMI en particular? – 

- Para averiguar el precio del AMI, visitamos la página de precios de AWS, o volvemos al menú superior Pricing -> Learn More About AWS pricing.

- Desplácese hacia abajo hasta la sección «Services Pricing» de la página y elija EC2″

- Aquí debemos elegir la región en la que estamos interesados en los precios y luego encontrar el AMI que queremos usar en la tabla. 

- En nuestro caso, estamos buscando t2-micro. Como podemos ver, si los primeros 12 meses gratuitos caducan o superamos las limitaciones de AWS, se nos cobrará 0.0116 USD por hora.


#
![Screenshot_10](https://user-images.githubusercontent.com/96561825/173657081-e0f9dadf-ee48-43bb-b9fc-d0222b03443c.png)

#



Sin embargo, si bajamos la tabla, podemos ver que hay imágenes de precios muy altos por hora. 

Por lo tanto, una buena práctica es siempre investigar el precio de un AMI antes de comenzar a usarlo, para que no tengamos sorpresas al final del mes!




#
#
## 3.4 Configurar EC2 User Data Script

Ahora que entendemos el pago, procedamos al siguiente paso para crear nuestra instancia EC2. Entonces, regrese a la pantalla donde la dejamos , elija la instancia
t2.micro y continue adelante.

Verá la siguiente pantalla que nos brinda la oportunidad de configurar los detalles de la instancia. 

Para este tutorial, no necesitamos sumergirnos en esto. Sin embargo, quiero mostrarle los detalles avanzados de esta página, en particular el User Data.

EC2 User Data representa un script que se ejecutará solo una vez después de que la máquina se inicie y nunca se ejecutará nuevamente. 

Es realmente fácil automatizar algunas tareas de arranque como instalar software particular, actualizaciones necesarias, descargando archivos comunes de internet etc.

***Importante: El User Data Script se ejecuta como root.*** 

Entonces, cualquier comando tendrá derechos de sudo, así que tenga cuidado.

Así que desplácese hacia abajo hasta la configuración avanzada de la pantalla actual y elija ejecutar el script como texto.

Para este ejemplo, incluyamos un script que instalará Apache Http Server y mostrará una página web simple.

Desplácese hacia abajo hasta la parte inferior de la página actual y abra las opciones avanzadas.

Luego inserte la siguiente secuencia de comandos en el cuadro de entrada de user data.


La primera línea  -   #!/bin/bash    -  es realmente importante y si no está allí, las siguientes líneas no se leerán.


***#!/bin/bash***

***sudo yum update -y*** 

***sudo yum -y install httpd -y*** 

***sudo service httpd start*** 

***echo "Hello world from EC2 $(hostname -f)" > /var/www/html/index.html***


#
La configuración debería verse así
#
![Screenshot_11](https://user-images.githubusercontent.com/96561825/173658074-09ed520e-760c-4085-9962-d7986ba952ff.png)
#
# 
#
![Screenshot_12](https://user-images.githubusercontent.com/96561825/173671661-db633f66-4b09-4e6e-99da-7072044ea4dc.png)
#

Los siguientes dos pasos «Add Storage» y «Add Tags» los podemos omitir por ahora. 

Así que vaya al paso 6 «Configure Security Group».


Lo importante es saber que el storage que tenemos (el storage local de archivos de la instancia) no persiste. 

Eso significa que si cierra la instancia, se pierde.

Hay soluciones a este problema.

Por ejemplo, podemos usar el Amazon Simple Storage Service (S3).

#
#
### 3.5 Configurar Security Group 

Un grupo de seguridad actúa como un firewall virtual para su instancia para controlar el tráfico entrante y saliente. 

Si no tiene ningún grupo de seguridad, le pedirá que cree uno de inmediato.

Entonces, de manera predeterminada, hemos habilitado el acceso SSH a la máquina, y agregamos un HTTP para que podamos acceder a nuestra página web. 

Para hacerlo, siga los pasos de la captura de pantalla a continuación.  

Tenga en cuenta que con las flechas 4 y 5 estamos configurando que podemos acceder a la máquina a través de SSH y HTTP desde cualquier otra dirección IP.

Para nuestro ejemplo no importa, pero en algunos proyectos serios, la práctica es permitir solo direcciones IP conocidas.

#
![Screenshot_16](https://user-images.githubusercontent.com/96561825/173659339-a032bb2a-94ea-42d8-91a5-c71cc1063a92.png)

#

![Screenshot_14](https://user-images.githubusercontent.com/96561825/173669648-881ba4b5-63ad-4e33-82c2-e6c460dc1baf.png)

#

![Screenshot_15](https://user-images.githubusercontent.com/96561825/173669670-1abe3e05-9c4e-450a-b777-f30f8806bd71.png)

#

![Screenshot_16](https://user-images.githubusercontent.com/96561825/173669677-7d20c204-6ba2-4640-b940-06341877354f.png)

#

![Screenshot_17](https://user-images.githubusercontent.com/96561825/173669683-a21748f7-8754-40bf-86a8-e78fa06629f1.png)

#

![Screenshot_18](https://user-images.githubusercontent.com/96561825/173669692-ecf4a6ff-5a9e-4212-b7eb-de26e4e42d6a.png)

#

![Screenshot_19](https://user-images.githubusercontent.com/96561825/173669703-5325e46a-a83a-4684-9281-4b2172b1533f.png)

#




#
#

### 3.6 Review and launch

En esta página vemos el resumen de nuestra instancia, haga clic en «botón de inicio» en la esquina inferior derecha y verá la siguiente pantalla, pidiéndole que cree un par clave-valor. 

#

![Screenshot_20](https://user-images.githubusercontent.com/96561825/173659622-04b1af34-5cda-4cbb-b179-656466a0e22e.png)

#


Eso será necesario si queremos conectarnos a la instancia desde nuestra máquina local. 

Porque, por supuesto, no tendremos una conexión de escritorio, por lo que esa sería la única forma de acceder a ella. 

Así que vamos a conectarnos a través de la línea de comando, y para identificarnos, necesitaríamos ese par clave-valor.

Entonces elija crear un nuevo par.

Luego inserte el nombre del par, descárguelo e inicie la instancia.

#

![Screenshot_21](https://user-images.githubusercontent.com/96561825/173659815-9383ed67-3b6a-437f-8109-24987169910b.png)

#




El archivo que acaba de descargar se requerirá explícitamente cuando intente acceder a la máquina a través de ssh.

¡Genial! 

¡La instancia que acaba de crear ahora se está iniciando! Para ver sus instancias EC2, haga clic en el botón «Ver instancias» que se muestra en la captura de
pantalla a continuación.

#

![Screenshot_13](https://user-images.githubusercontent.com/96561825/173660069-fe0d8d29-87e8-41df-aece-77bd7482f525.png)

#



#
#
## 4. Observar la instancia en ejecución


Ahora, en esta página, debería ver su instancia EC2 arrancando. 

Allí podemos ver su estado, su IP pública e información adicional.

Además, podemos realizar acciones como start, stop o terminate (es igual a eliminar). 

La instancia no tendrá nombre, así que simplemente haga clic en la columna de nombre para cambiarla.

#

![Screenshot_23](https://user-images.githubusercontent.com/96561825/173665814-26daeb62-e15b-412b-a44b-e8d44b68662e.png)

#



Entonces, para acceder a nuestro servidor web, simplemente debemos copiar la dirección IP pública de la máquina y pegarla en el navegador. 

Es importante que se espera a que el estado de la máquina sea «running» y que las «status checks» sean 2/2.

De lo contrario, puede intentar acceder a él mientras todavía se está iniciando, por lo que no podrá. 

Tenga en cuenta que cada vez que reiniciemos nuestra instancia, recibirá una IP pública diferente.

#

![Screenshot_24](https://user-images.githubusercontent.com/96561825/173660445-407c63b0-1314-422a-9852-5e65a279dd32.png)

#

Bien, acabamos de acceder a la página web que creamos usando el script de User Data.


#
#
## 5. SSH Access
#


Para acceder a la máquina a través de SSH, abre la terminal y ejecuta el siguiente comando: Para acceder a la máquina a través de SSH, abre la terminal y ejecuta el siguiente comando:

***ssh -i /path/to/key/value/pair/my_instance_access.pem***
***ec2-user@instance_public_ip***

#
![Screenshot_25](https://user-images.githubusercontent.com/96561825/173665999-ba9d4308-1576-49d3-8c75-8fc4671400e9.png)
#

Una vez que accedemos a la máquina, podemos verificar que lo hemos hecho todo correctamente, ejecuta el siguiente comando


***cat /var/www/html/index.html***

#
![Screenshot_26](https://user-images.githubusercontent.com/96561825/173666077-c1ff7cf7-08a6-4537-9d46-113d1c15e865.png)
#




#
#

### Importante: 
### En algunos casos, es posible que salga un error indicando que no tienes permisos para acceder al archivo «.pem». Entonces, ejecute chmod 400 contra el archivo.
### Establecerá – a + rwx, u-wx, g-rwx, o-rwx. 
### Esto significa que el usuario / propietario puede leer, no puede escribir y no puede ejecutar. 
### Los grupos y los otros usuarios no tienen ningún permiso.

#
#


Deberías recibir el siguiente resultado

#
![Screenshot_27](https://user-images.githubusercontent.com/96561825/173666404-36b1c33d-6e8e-4f71-9bd9-8ea3aa057b87.png)
#



#
#

## 6. Conclusión


Acabamos de crear nuestra primera instancia de EC2 en AWS, pasando por el proceso lentamente con la comprensión de los puntos clave.

Además, hemos entendido cómo funcionan los precios. 

Cómo acceder a la máquina a través de ssh y configurar el acceso SSH y HTTP a través de la configuración del grupo de seguridad.

Ahora podemos proceder a ejemplos más específicos y ampliar nuestro conocimiento de AWS. 

Cuando termine de usar las instancias, no olvide detenerlas para evitar cargos adicionales

#

Por ultimo, crearemos una snapshot, atendiendo a las siguientes instrucciones accedemos a AWS > Services > EC2 > Volumes buscamos el servidor al que queremos realizar
el snapshot e identificamos los volúmenes asociados a la instancia.
#


#
![Screenshot_31](https://user-images.githubusercontent.com/96561825/173672944-a25f2e4b-8e29-4c22-b2e1-17f836b83769.png)
#


Una vez anotados los volumenes nos vamos a la pestaña snapshost >
#
![Screenshot_33](https://user-images.githubusercontent.com/96561825/173666863-e236bd01-b2b0-479f-ba2b-c69a0d8b974b.png)

#

Nos abre un asistente de configuración en el que indicamos el volumen y asignamos un nombre y una descripción.
#
![Screenshot_34](https://user-images.githubusercontent.com/96561825/173666839-fd3d64f9-47af-41b5-b493-b5e0520a3f31.png)


#
![Screenshot_32](https://user-images.githubusercontent.com/96561825/173673015-a198dd39-38f3-4289-8a04-b8dc03048c81.png)

#
#
#
#
#

Seguimos en el [Día 46](day46.md)
