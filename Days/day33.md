

# Certificados en la práctica

#
#
## Objetivos


En el siguiente ejercicio vamos a hacer uso de la criptografía viendo cómo funciona un certificado. Para ello, vamos a ir a nuestra VPC de AWS, generaremos un dominio propio en ***www.noip.com*** y seguiremos este tutorial paso a paso que contiene todo lo que vamos a necesitar para completar el ejercicio.



## Instrucciones![Screenshot_44](https://user-images.githubusercontent.com/96561825/173273022-7efbeba0-3a3a-478a-8d57-7247833ef0de.png)


1) Creación de la instancia EC2 en la VPC.
2) Generación del dominio en noip. 
3) Generación del certificado SSL en Let's Encrypt.


#
#
## 1- Creación de la instancia EC2 en la VPC

### Acceso a la consola de gestión AWS

Una vez logueados en la consola de Amazon Educate, seleccionamos la opción ***AWS Account***. Allí aparecerá listada la materia y hacemos clic en ***Go to Classroom***.

![Screenshot_3](https://user-images.githubusercontent.com/96561825/173269381-366d38c8-fb8d-4bbd-9a2c-558dbbfcee06.png)

#
Seleccionamos  la opción ***AWS Educate Starter Account***.


![Screenshot_4](https://user-images.githubusercontent.com/96561825/173269387-fc01cbc6-ad05-4622-97d9-bc02353d065a.png)

#
Luego, presionamos el botón de acceso a ***AWS Console***  y verificamos que el navegador no bloquee ventanas emergentes en este sitio.

![Screenshot_5](https://user-images.githubusercontent.com/96561825/173269661-daa4fb7c-32b7-47e1-bc25-beedd0f6bf72.png)
#
Nos encontramos con la consola de gestión de la plataforma AWS.

![Screenshot_6](https://user-images.githubusercontent.com/96561825/173269710-d1db6f3d-009f-414c-8b1d-d96e56c3a5ab.png)
#
Una vez allí, hacemos clic en EC2.


![Screenshot_7](https://user-images.githubusercontent.com/96561825/173269770-8ad1deca-676a-41a0-bee3-3f4d22879673.png)


#
#
## Crear una instancia en EC2

Nos posicionamos en la parte superior derecha de la pantalla y hacemos clic en el botón ***Launch instances***. 

![Screenshot_8](https://user-images.githubusercontent.com/96561825/173269946-9385d08f-9f0b-4c42-a26f-08f883e3c672.png)
#
Luego, elegimos Ubuntu Server 20.04 LTS.

![Screenshot_9](https://user-images.githubusercontent.com/96561825/173269995-18a35323-8b7d-4279-8e77-59eafca4becd.png)

#
Seleccionamos el modelo de máquina ***Family T2.micro (capa free)*** 

Y hacemo clic en NEXT .


![Screenshot_10](https://user-images.githubusercontent.com/96561825/173270124-a8346d5b-ac70-4eb4-ada3-60c83703177c.png)

#

En la interfaz, el Step 3 lo dejamos tal cual está y apretamos ***Next***. 

En el Step 4, dejamos los discos por defecto de 8 GB, volvemos a presionar Next. 

En el Step 5, hacemos lo mismo. 

Mientras que en el Step 6 vamos a configurar, por ahora, un grupo de seguridad para el acceso a la instancia.

![Screenshot_11](https://user-images.githubusercontent.com/96561825/173270193-fbb463d2-ff00-4011-ad63-7f1e472f8da6.png)
#

Lo importante es darle un nombre y una descripción que nos ayude a identificarlo y dar acceso a los protocolos.

![Screenshot_12](https://user-images.githubusercontent.com/96561825/173270222-da957f28-800f-4953-9ec4-7ed3858a6a4f.png)


Hacemos clic en ***Review and Launch***.

Corroboramos la configuración de la instancia y hacemos clic en ***Launch instances***.

![Screenshot_13](https://user-images.githubusercontent.com/96561825/173270263-be1c39f3-e0ea-4079-8ed3-65846ce58f5f.png)

#

Creamos un nuevo key pair, si no tenemos, y descargamos el archivo ***.pem.***

![Screenshot_14](https://user-images.githubusercontent.com/96561825/173270311-4a190c0b-7f45-4451-9723-9848767c831a.png)





#
#
# Instalar Apache


Para este apartado vamos a necesitar una consola o terminal Bash para comunicarnos vía SSH.

En la actualidad, hay muchos productos disponibles y depende del sistema operativo que estemos utilizando. 

Por el momento, dejamos a tu criterio cuál te parece más cómodo y agradable a la vista.

En este ejemplo, utilizamos Windows 10 con Cmder. 

En caso de no tenerlo, se puede descargar de https://cmder.net —recomendamos bajar la versión full que es totalmente portable—. 

Copiamos el archivo de claves ***.pem*** en la carpeta raíz del Cmder, solo por comodidad del ejemplo. 


Abrimos la consola. 

En la parte inferior derecha abrimos un bash como administrador.

![Screenshot_15](https://user-images.githubusercontent.com/96561825/173270439-01f01caf-0c3c-479e-a491-b12f46ab518b.png)

Vamos a buscar la IP de la “Instancia01” que está online.

![Screenshot_16](https://user-images.githubusercontent.com/96561825/173270447-61b48f91-1940-470d-9288-3a3bad4a5bb0.png)

![Screenshot_17](https://user-images.githubusercontent.com/96561825/173270494-73316736-4e21-4954-9a8f-5a60ce372fba.png)


Una vez dentro, tenemos que instalar un servidor Apache para deployar nuestro código. 

Con este objetivo, ponemos el siguiente comando:

![Screenshot_18](https://user-images.githubusercontent.com/96561825/173270528-e93c6788-d5ce-4089-90fe-0e4b7b0bdc12.png)


Comprobamos que el servicio esté andando.

Ingresamos a un explorador y colocamos la IP de nuestra instancia y nos debe contestar: ***Apache2 recientemente instalado***

![Screenshot_19](https://user-images.githubusercontent.com/96561825/173270592-571def0d-fee3-43e1-8e1f-df05d89b84dc.png)


Luego, clonamos el repositorio del proyecto  En este caso, lo tenemos en el repositorio público de Github.


![Screenshot_20](https://user-images.githubusercontent.com/96561825/173270616-a4fa23c8-3608-4d56-a445-0af06b1f679c.png)


Ingresamos nuevamente a la instancia a través del navegador web.

![Screenshot_21](https://user-images.githubusercontent.com/96561825/173270662-0ddf7172-6db6-4657-93c7-5ce097b968cf.png)














#
#
# 2 - Generación del dominio en noip


Ingresamos en nuestro navegador a ***www.noip.com***.


Luego, creamos nuestro nombre de dominio propio. 

Vale la pena aclarar que en este punto tenemos que colocar nuestro nombre único de dominio para poder redireccionar a nuestra EC2.

Tendremos que crear un registro en el sitio web y crear el registro gratuito.

![Screenshot_22](https://user-images.githubusercontent.com/96561825/173270814-0bec88ee-6754-481f-91fe-51ff1640e5f4.png)

Confirmamos en nuestra casilla de correo electrónico y luego vemos lo siguiente:

![Screenshot_23](https://user-images.githubusercontent.com/96561825/173270878-775a5a06-5885-432a-8110-257042ad9aab.png)


Iniciamos sesión en www.noip.io , luego nos dirigimos en el menú de la izquierda a DNS Dinámico y finalmente Nombre de host sin IP.

![Screenshot_24](https://user-images.githubusercontent.com/96561825/173270914-c6cff398-25b3-4ba9-9059-0738069ebd3b.png)


Modificamos el dominio que creamos con la IP de la instancia de EC2 que creamos.
![Screenshot_25](https://user-images.githubusercontent.com/96561825/173270941-37aba87f-8f68-4dd4-9920-a109cfa89648.png)



Damos en actualizar, y ¡listo! Ya tenemos nuestro domino online. 

En este caso, devopsddns.net (recordá que este es el ejemplo que utilizamos para este tutorial.

No podés usar este mismo dominio porque ya está ocupado)


![Screenshot_26](https://user-images.githubusercontent.com/96561825/173270981-a3aa95da-74d0-4599-9cdb-bb8fd317527c.png)






#
#
# 3 - Generación del certificado SSL en Let’s Encrypt 
#

## Instalar Certbot

El primer paso para utilizar Let's Encrypt para obtener un certificado SSL es instalar el software Certbot en el servidor. Para ello ingresamos nuevamente a nuestra 
instancia EC2 por medio de nuestro archivo .pem en la AWS. 

Luego, instalamos las dependencias necesarias:

![Screenshot_27](https://user-images.githubusercontent.com/96561825/173271092-41c874c1-c78a-49c5-b76a-984e08c6659c.png)


Comprobamos la presencia del repositorio de universe.

![Screenshot_28](https://user-images.githubusercontent.com/96561825/173271098-0211b8d7-3054-4287-8172-56f05585951b.png)

Nuevamente actualizamos la lista de paquetes disponibles.

![Screenshot_29](https://user-images.githubusercontent.com/96561825/173271102-5e2a3df0-b578-4d79-8cb6-a5454f94bb02.png)



#
## Certbot para Apache

Ejecutamos este comando desde nuestra la línea de comandos para instalar Certbot:


![Screenshot_30](https://user-images.githubusercontent.com/96561825/173271111-6f3b652a-e2a2-46b5-ab5c-ded88d7bc274.png)

#
## Configuración de firewall (UFW)


Si el firewall UFW está habilitado, debemos crear una nueva regla para permitir el tráfico HTTPS. Para verificar si el firewall está activo, ejecutamos este comando:

![Screenshot_31](https://user-images.githubusercontent.com/96561825/173271117-c83ba911-960f-4f82-b780-df9649efb211.png)



Para permitir el tráfico HTTPS para Apache:


![Screenshot_32](https://user-images.githubusercontent.com/96561825/173271336-d0b725ba-8161-403a-934d-5722e9276449.png)


#
## Obtener un certificado SSL


Certbot utiliza el complemento Apache para obtener certificados SSL:

![Screenshot_33](https://user-images.githubusercontent.com/96561825/173271355-f7f51314-1f85-45cf-842b-d85856434b3e.png)




Nos va a pedir un mail para registrarnos, y la configuración de los directorios que podemos responder “mail”,“y” y “a”.


![Screenshot_56](https://user-images.githubusercontent.com/96561825/173274203-2d67921b-a3a2-4a68-9128-563ea6d57a45.png)


![Screenshot_57](https://user-images.githubusercontent.com/96561825/173273908-7515592a-d576-4be2-b528-7d2aa9ed2701.png)

![Screenshot_58](https://user-images.githubusercontent.com/96561825/173273898-821b3650-7721-45b6-8df7-29514ee3347b.png)

![Screenshot_59](https://user-images.githubusercontent.com/96561825/173273884-b6d29ea0-c69b-405c-bb0f-58156a57d2cc.png)

![Screenshot_61](https://user-images.githubusercontent.com/96561825/173273877-8f4bf6e5-9651-4eed-a0e1-87dae5fe9698.png)

![Screenshot_62](https://user-images.githubusercontent.com/96561825/173273869-0efbe615-93fb-4c35-8afc-9b0247450239.png)

![Screenshot_63](https://user-images.githubusercontent.com/96561825/173273867-e953a319-f865-483b-a779-771681659410.png)



La ejecución de este comando permitirá obtener un certificado SSL y Certbot modificará automáticamente la configuración de Apache. De lo contrario, podríamos obtener el certificado SSL y luego configurar Apache manualmente con el siguiente comand

![Screenshot_48](https://user-images.githubusercontent.com/96561825/173273262-22f52f27-3fec-4db1-b45b-bbc0f14c9219.png)



Ingresamos nuestro dominio, en este casodevops***.ddns.net.***



![Screenshot_64](https://user-images.githubusercontent.com/96561825/173274420-20e91258-13e5-4852-82e1-24fc48a39ef7.png)

![Screenshot_65](https://user-images.githubusercontent.com/96561825/173274414-42ace3d4-37cc-429b-bb31-f4f3a23871a7.png)


![Screenshot_66](https://user-images.githubusercontent.com/96561825/173274408-f8001b9d-28fa-4b32-bdad-34d02aaa49d0.png)

#
#
# Renovación automática (opcional)


Los paquetes de Certbot vienen con un trabajo Cron que renovará automáticamente sus certificados antes de que caduquen. Dado que los certificados Let's Encrypt duran 90 días, se recomienda encarecidamente aprovechar esta función. Podemos verificar la renovación automática de certificados ejecutando este comando:

![Screenshot_45](https://user-images.githubusercontent.com/96561825/173273102-4994c8f4-c99f-47e4-a62f-2b08bfff8577.png)


El comando para renovar Certbot se instala en una de las siguientes ubicaciones:


![Screenshot_44](https://user-images.githubusercontent.com/96561825/173273076-2becc60e-c8aa-4896-99c8-bc6be956a3ae.png)



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
