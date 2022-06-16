
# BootCamp DevOps Engineer
#

#

# [Desafio 1 AWS ]( https://misdiasdedevops.github.io/Fase-1/Days/AWS-Desafio-1.html)  En formato SLIDES
#
#


# CREACION y SECURACION de tu CUENTA

### Iniciamos con la creacion de una cuenta en AWS.

Paso 1: Nos dirigimos al portal de Azure ubicado en https://aws.amazon.com/es/,  iniciamos sesion.

#

![image](https://user-images.githubusercontent.com/96561825/173444793-ce06ed4b-bb3c-4366-b1a1-8f18eb96668b.png)

#

## Paso 1 – Create an AWS account
#
Seremos  dirigidos a la página de iniciar sesión o a la de crear cuenta.  No se deben  preocupar  por la selección entre «Root y IAM user».  Lo veremos más tarde. 

Ahora solamente  hacer clic en «Create a new AWS account» y vas a ver la pantalla siguiente.

#

![image](https://user-images.githubusercontent.com/96561825/173444849-2ed623eb-d61c-488b-b0f2-1c6bc05f6486.png)

#

## Paso 2 – personal data


Despues veremos la siguiente pantalla. 
#
![image](https://user-images.githubusercontent.com/96561825/173444871-81f34296-de27-49ae-8990-41c6ad2567a4.png)
#

Completamos los datos y nios pide verificar el email, continuamos
#
![image](https://user-images.githubusercontent.com/96561825/173444979-f74ffe6a-5806-4819-91e3-26d59eade432.png)

Vamos a nuestro correo para verificar el codigo, 

#
![image](https://user-images.githubusercontent.com/96561825/173444995-e436e741-7f27-481e-a04b-d9020e7de10e.png)
#

ahora debemos proporcionar este dato en la pagina principal

#
![image](https://user-images.githubusercontent.com/96561825/173445048-56efaea4-820b-4109-a3f8-0a5e24defcbf.png)

#

Y pasamos al siguiente paso  donde registramos en AWS con contraseña , 
#
![image](https://user-images.githubusercontent.com/96561825/173445087-2e4fba5a-a612-48f7-99cc-bd05b620876e.png)

#
Prestar atencion a las exigencias de la contraseña 
#
![image](https://user-images.githubusercontent.com/96561825/173445136-f5973050-446a-44a0-a361-fa2fa3d5b161.png)
#



#

Continuamos completando con los datos requeridos
#
![image](https://user-images.githubusercontent.com/96561825/173445164-8d7e9f2e-1012-47a2-b63a-55db55c0b1bf.png)
#

Completamos y seguimos completando
#
![qq](https://user-images.githubusercontent.com/96561825/173446507-a604106a-cec4-4a0d-9b6f-2053fdf6c484.png)
#
## Paso 3 – payment details

Seguimos 
#
![image](https://user-images.githubusercontent.com/96561825/173446604-725bf660-76fd-4323-8022-fc711b8547ea.png)
#

## Aviso: 
## Se recomienda encarecidamente que no utilice el usuario root para sus tareas diarias, incluso las administrativas. 
## En cambio, adhiérase a la mejor práctica de usar el usuario raíz solo para crear su primer usuario de IAM. 
## Luego, bloquee de forma segura las credenciales de usuario raíz y úselas para realizar solo unas pocas tareas de administración de cuentas y servicios. 

#

***IAM significa Identity and Access Management**. Le permite administrar el acceso a los servicios y recursos de AWS de forma segura. 

Utilizando IAM, puede crear y administrar usuarios y grupos de AWS, y usar permisos para permitir y denegar su acceso a los recursos de AWS. 

Así que ingresemos a la consola de AWS como usuario ROOT, ingresando el correo electrónico que utilizamos para registrarnos. 

#
#

Aclaracion Importante: 
#

Debido a que ya tengo una cuenta creada bajo otra denominacion y para que no haya problemas de solapamiento y/o  conflicto  con la tarjeta,   ya que solo poseo una sola tarjeta,  aquí suspendo el proceso de la registracion. 

Fin de esta proceso. 

#
#
#

## 5. Securizar la cuenta


Como una buena práctica debemos  inmediatamente después de iniciar sesión es  securizar nuestra cuenta de AWS. 

#
![image](https://user-images.githubusercontent.com/96561825/173447579-9fb3faf8-5804-4d7f-a14f-35712923d6e5.png)
#

En la barra de búsqueda, escribimos IAM 

#
![image](https://user-images.githubusercontent.com/96561825/173447605-ffeec8df-8434-4447-8313-b9101c16d4c0.png)

#

y seleccionamos el resultado que aparece.

#
![image](https://user-images.githubusercontent.com/96561825/173449138-83ccd545-868f-4b2f-abd1-91dced699257.png)

#
Activamos MFA –multi factor autentificacion , en la pantalla de IAM, haz click en «ACTIVAR MFA»

#
![image](https://user-images.githubusercontent.com/96561825/173449221-2a23b9c5-c1a2-47a4-84da-a39368bb7e44.png)
#


En la pantalla que nos aparece, apretamos “ DISPOSITIVIO MFA VIRTUAL” 

#
![image](https://user-images.githubusercontent.com/96561825/173447666-1d03c717-d0a4-49ef-b982-b713f6e9cae1.png)
#

Paso 1 – Activate MFA (multi-factor authentication) on your root account

A posteriorla  la aplicación de autenticación de Google nos muestra el código QR que escanearámos en nuestro celular ..

Para ello debemos tener instalado el programa Google Authenticator o similar .


#
![image](https://user-images.githubusercontent.com/96561825/173447725-fbe54f8b-feaa-4e09-9d36-e3d2537bc4a1.png)
#


Entonces, la aplicación nos dara una nueva clave cada unos segundos.

Introduzca las 2 claves generadas en secuencia por el autenticator en su móvil y pulse siguiente.

#

Al concluir,  deberíamos  lograr ver la siguiente pantalla:

#
![image](https://user-images.githubusercontent.com/96561825/173447798-4c8bfc30-fabe-459e-9aac-2011f11f1f74.png)
#


#
#

## Paso 2 - Create IAM user
#
## Create IAM user
#

Primero, hablemos de los usuarios en cuestión de AWS.

Acabamos de crear e iniciar sesión en nuestra cuenta, digamos nuestra organización. 

Allí podemos crear diferentes usuarios, de diferentes grupos, con diferentes permisos. 

Supongamos que tiene 1 administrador, 3 desarrolladores, 1 operaciones de desarrollo y un administrador. 

Todos estos usuarios estarán asociados a la cuenta que acabamos de crear e ingresó como root. 

Entonces, asegurémonos de que el acceso y los permisos funcionan. 

Tenemos grupos, tenemos usuarios, roles y políticas. 

Podemos verlo a la izquierda de la pantalla. 

Creemos un nuevo grupo de administradores, con derechos de administrador completos. 

Vayamos a grupos y hagamos clic en Crear nuevo grupo. 

Demos el nombre del grupo «admins», y luego veremos el siguiente paso que consiste en adjuntar políticas al grupo. 

#
![image](https://user-images.githubusercontent.com/96561825/173447888-c2de2f29-8033-4d54-b484-cbd5df15ad52.png)

#

Aquí la elección del tipo de acceso es importante. Tenemos dos opciones:

● Acceso programático es un tipo de acceso desde la interfaz de línea de comandos de AWS utilizado por los desarrolladores. 

Por ejemplo, para insertar código en AWS o ejecutar otros comandos relacionados con la programación.

● Acceso a la consola de administración de AWS es básicamente un tipo de acceso para usuarios que solo acceden a la consola que estamos usando en este momento para monitorear o administrar.

Entonces, después de elegir el tipo de acceso (en este caso, solo acceso a la consola), debemos elegir una contraseña para el usuario y continuar. 

La siguiente pantalla nos dará la oportunidad de asignar al usuario a un grupo.

Vamos a asignarlo a nuestro grupo de administradores.

#
![image](https://user-images.githubusercontent.com/96561825/173447911-aef4fe79-8a3d-4351-bb28-d657e0a2c991.png)

#

Creamos un usuario

![image](https://user-images.githubusercontent.com/96561825/173447964-dcbcf451-69b3-4396-b9f6-e541ff4029c8.png)

#

Le damos permisos
#
![image](https://user-images.githubusercontent.com/96561825/173447994-311e11ca-f3d6-465d-b0c1-ff5a7200233a.png)

#

Si todo esta correcto obtendremos la siguiente pantalla.
#
![image](https://user-images.githubusercontent.com/96561825/173448029-357c98a8-d898-41fb-a81d-28bd7c35f4d3.png)
#

Cuando usamos el botón de abajo «Descargar.csv» todos los detalles de la tabla se van a descargar. Incluso el enlace de login.

#
![image](https://user-images.githubusercontent.com/96561825/173448062-d9409047-f99c-457a-996a-c67a7921f46c.png)

#

Usuario creado exitosamente.
#
![image](https://user-images.githubusercontent.com/96561825/173448120-e54658b3-46ae-4c89-acc1-eeebbee9b6fa.png)

#

Como acabamos de crear nuestra cuenta, que ya tiene autenticación de dos factores, no hay necesidad de “Aplicar una politica de contraseña IAM”,  no se tiene que hacer este paso.

#
![image](https://user-images.githubusercontent.com/96561825/173448155-b7ec52eb-3417-4910-a0f3-4eeb57a9b177.png)
#

#
## 6 . Crear un presupuesto para la cuenta y activar una alerta 
#
## CREAR UN PRESUPUESTO 
#

Iniciamos sesión en la consola como el usuario root (porque es el único que tiene acceso a la información de facturación).

Luego en la barra de búsqueda de la consola de administración de AWS, escribimos «Facturacion » y elija en el resultado que aparece “Budget”

#
![image](https://user-images.githubusercontent.com/96561825/173448228-bffa9464-3f01-46cb-b0c1-f7e998e59456.png)

#

Creamos nuestro propio presupuesto.

![image](https://user-images.githubusercontent.com/96561825/173448272-330d0267-7085-4f79-b46e-f18eb1a382af.png)

#

Definimos el presupuesto.
#
![image](https://user-images.githubusercontent.com/96561825/173448316-7834a389-3968-4296-bcf6-03021d14d278.png)

#

Lo definimos mensualmente y con un importe de 5 dolares .

#
![image](https://user-images.githubusercontent.com/96561825/173448357-2a8a1726-6c34-4c01-98cd-9309891ac5bf.png)

#

Siguiente

#
![image](https://user-images.githubusercontent.com/96561825/173448400-73d160ef-9fc5-4a74-a3e5-7c936b1b070b.png)
#

Aquí aclaramos que nuestro presupuesto mensual es de 5 dolares , y cada vez que superemos los 2.50 dolares recibiremos un correo notificandonos.

#
![image](https://user-images.githubusercontent.com/96561825/173448422-c9c4b0f1-bdf0-4818-a9a3-082dbb019de6.png)
#

Aquí operamos la alerta del 50% 

![image](https://user-images.githubusercontent.com/96561825/173448472-2135b268-ca69-4657-bf13-b91225faba41.png)

#

Aquí tenemos una informacion detallada de nuestro presupuesto y como lo vamos a manejar.


#
![image](https://user-images.githubusercontent.com/96561825/173448507-e624b1bc-f654-4f2c-907b-e450f4239420.png)
#
#
![image](https://user-images.githubusercontent.com/96561825/173448527-cebbe417-4775-4245-bbf8-562943e2f419.png)
#
Finalmente tenemos una cuenta segura en AWS que está lista para  propósitos de prueba, investigación y aprendizaje

Fin.
#
#
## 7. Conclusión
#

En conclusión, tenemos una cuenta segura en AWS que está lista para algunos propósitos de prueba, investigación y aprendizaje.

Entendemos cuál es la diferencia entre un usuario raíz y un usuario de IAM, cómo podemos crear un usuario y asignarlo a un grupo con un permiso específico.

Hemos activado la autenticación de 2 factores para asegurarnos de que nadie se rompa incluso si la contraseña está expuesta. 

Hemos manejado la parte de pago y hemos configurado un presupuesto y una alerta, para que podamos ser notificados si cometemos ciertos errores y se nos cobra. 

El siguiente paso es aprender más sobre la terminología en AWS y luego comenzar a jugar con algunos de sus servicios.
#
#
#
#
#
Seguimos en el [Día 41](day41.md) 
