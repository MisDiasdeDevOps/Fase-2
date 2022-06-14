
BootCamp DevOps Engineer


Máquinas Virtuales en
AZURE



Desafío 3 Azure
Desafío 1 Semana 1 
Máquinas Virtuales en Azure
Alumno  Marcelo Piroddi 
Profesores Gino Rojo – Gastón Baravalle

#
#

### Inicio de sesion en Azure

Paso 1

Nos dirigimos al portal de Azure ubicado en https://portal.azure.com ,  e iniciamos sesion.

Paso 2

Escribimos en la seccion de busqueda ; “maquinas virtuales” , a partir de alli seleccionamos “Crear” y se abrira la pagina con los detalles para la creacion de una maquina virtual.

Si hemos procedido correctamente veremos una pagina con el texto “Crear de maquina virtual”, como la siguiente imagen.


![image](https://user-images.githubusercontent.com/96561825/173630012-76187b1d-0000-4436-9b2d-7230a5172746.png)

#
Paso 3

Recién comenzamos, debemos seleccionar la suscripción indicada y a esta máquina virtual debemos darle nombre. Usaremos los detalles que nos informa la imagen para completar los espacios.


![image](https://user-images.githubusercontent.com/96561825/173630082-21f3f5a1-ae34-4a35-83ad-a56869a8225f.png)

#

Paso 4

Completamos los detalles de instancia, guiándonos con los datos como aparecen en la imagen.

![image](https://user-images.githubusercontent.com/96561825/173630133-37e2af07-0bcf-4b87-9f53-966bf58aecb6.png)

#

Paso 5

En la sección cuenta de administrador darle un usuario y contraseña. Usamos los datos que aparecen en la imagen.

![image](https://user-images.githubusercontent.com/96561825/173630161-66418b67-8495-4646-bd61-8d247a394032.png)

#

Pasó 6

Habilitamos en la sección “Reglas de Puerto”, los puertos RDP 3389 y HTTP 80.

![image](https://user-images.githubusercontent.com/96561825/173630223-e6151057-b90a-48cc-ad9c-f2aaa64e877d.png)

#

Paso 7

A veces da error, volver a insistir. Refrescar la página es también una opción.

En el peor de los casos empezar de nuevo.

A veces Azure tiene estos problemas.

![image](https://user-images.githubusercontent.com/96561825/173630365-eda603cc-49b8-480f-929a-eeccd04c1cb7.png)
 
 #
 
Paso 8

Ya estamos pronto a finalizar, Máquina virtual creada

![image](https://user-images.githubusercontent.com/96561825/173630434-02a46f37-ff67-4b07-96bc-d8f8bde284a1.png)

Se están implementando los cambios, paciencia

#


![image](https://user-images.githubusercontent.com/96561825/173630473-c46491cb-38b7-4adf-be33-df883ba9fb12.png)

Cambios implementados, listo.

#

![image](https://user-images.githubusercontent.com/96561825/173630568-959305f8-fa3a-456c-8e7b-020ea4a3e045.png)

Una vez finalizada la implementación, seleccionamos “Ir al recurso”

#

#
#
#

Ejercicio Conexión a la máquina virtual

Vamos a crear una conexión a Escritorio remoto en la máquina virtual,  lo que nos permitirá conectarnos a la máquina virtual desde un equipo  de Windows.

En la imagen siguiente seleccionamos Conectar RDP.


Y descargamos el archivo RDP


![image](https://user-images.githubusercontent.com/96561825/173630826-b1369976-af7b-4507-8298-ac912b32b7ad.png)

el archivo RDP una vez descargado veremos la siguiente imagen;

#


![image](https://user-images.githubusercontent.com/96561825/173630891-eecba641-5131-43fa-a137-1881d844d4c3.png)

Hacemos doble clic en el archivo y nos aparecerá esta ventana, damos “Conectar” y seguimos

![image](https://user-images.githubusercontent.com/96561825/173630950-461c8145-363d-4796-9383-255e80263e74.png)

Al abrir el archivo veremos “ Seguridad de Windows” en el margen superior izquierdo 

#

Seleccionamos “Más opciones”  y, después, “Usar otra cuenta”.  

Allí escribimos  “Nombre de usuario” como localhostusername,  escribimos la contraseña que creamos para la máquina virtual y, luego, hacemos clic en Aceptar.

![image](https://user-images.githubusercontent.com/96561825/173631024-cf590d11-775e-45b4-af6f-e1a6c5d66992.png)


#

Al conectarse podremos ver la siguiente imagen .


![image](https://user-images.githubusercontent.com/96561825/173631130-ad63a6e0-6c91-42b7-b459-160e7daeb282.png)

![image](https://user-images.githubusercontent.com/96561825/173631158-6785be7f-1f5b-4c8c-b248-98dcad32110f.png)


#
#

PAGINA PRINCIPAL DE
 IIS
Vamos al portal de Azure, seleccionamos  la máquina virtual que creamos, en la información general de la máquina virtual,  mantenemos  el mouse sobre la dirección IP para mostrar el texto “Copiar al Portapapeles”.
Copiamos la dirección IP y la pegamos en una nueva pestaña de nuestro explorador.
Se abrirá la página de bienvenida de IIS predeterminada, y debería tener el siguiente aspecto .

Pero lamentablemente eso no paso.
Usamos dos exploradores diferentes, Google Chrome y Microsoft Edge, con resultado negativo.



![image](https://user-images.githubusercontent.com/96561825/173631232-0988f6a5-0ea3-4fe8-a8d6-3cc3750f54a2.png)



#


Seguimos buscando soluciones, posible problema Windows no tenga activado la compatibilidad con “IIS 6”.

Vamos para allá  ➽ Panel de Control  ➽ Programas y Características ➽ Activar o desactivar las características de Windows ➽ Controlamos.

![image](https://user-images.githubusercontent.com/96561825/173631295-79155587-4081-4fde-a0f5-b0d3b4e1f7f8.png)

#

Activamos las pestañas como se ven en la pantalla y veremos a continuación al aceptar .


![image](https://user-images.githubusercontent.com/96561825/173631368-4584c808-fcca-480a-831f-8d66a0619aa8.png)

controlar que este activado, escribimos en nuestro explorador “localhost” y deberíamos recibir como respuesta la siguiente imagen si esta todo correctamente realizado.


![image](https://user-images.githubusercontent.com/96561825/173631441-2a208487-8440-47ad-b833-70e1657541dd.png)

Probamos de nuevo

#

![image](https://user-images.githubusercontent.com/96561825/173631508-acfc3082-bed7-4b87-9a60-7ca93e7428ab.png)


Y el resultado sigue siendo negativo.

Buscamos otro camino, creamos una IP publica dentro de AZURE y se la añadimos a nuestra VM


![image](https://user-images.githubusercontent.com/96561825/173631556-07f22061-2c24-48a1-b697-2ceaa5a5f9ef.png)

#


![image](https://user-images.githubusercontent.com/96561825/173631587-1334b4b7-1536-46cb-ac36-d8f7cb35565b.png)


Probamos haciendo PING desde CMD y negativo

![image](https://user-images.githubusercontent.com/96561825/173631615-8b7a8c80-bec1-4c09-910c-c90ac3907ee7.png)


#



Seguimo buscando soluciones.  Nos vamos a este blog, donde nos indica …

![image](https://user-images.githubusercontent.com/96561825/173631671-97167e7e-ff74-41fd-985c-0d5caea18943.png)


#


Que si tenemos resultados negativos con el PING, podemos utilizar métodos alternativos, como usar la POWERSHELL con el comando “ Test-NetConnection”.
Probamos.
Resultado negativo.
Seguimos averiguando.


![image](https://user-images.githubusercontent.com/96561825/173631711-28cb223b-584c-4570-a8aa-b569d5699f7e.png)


#


Vemos de actualizar POWERSHELL y seguimos ,

![image](https://user-images.githubusercontent.com/96561825/173631752-a087bad5-42b4-4023-b087-cf4ac225b1bc.png)

![image](https://user-images.githubusercontent.com/96561825/173631770-bfeff974-c7b8-4de4-b555-2ce2c504f55e.png)

#

![image](https://user-images.githubusercontent.com/96561825/173631819-54939b00-d424-4374-a414-2fd746f289a0.png)

Terminamos de instalarla y probamos

![image](https://user-images.githubusercontent.com/96561825/173631868-b94ebf04-eb3c-4629-920d-dbc1d6a05033.png)

Resultado negativo, no reconoce el comando.

#

Seguimos buscando soluciones, otra posibilidad es hacer Ping con PSPing de Sysinternals Tools, es una de las herramientas incluidas en las PsTools .

Descargamos el archivo PSPing.exe y lo guardamos en Equipo , Disco local C, Windows, System32 , como muestra la imagen .

![image](https://user-images.githubusercontent.com/96561825/173631986-d676a423-7add-4848-8ef2-c269b9e5d8b9.png)

Ejecutamos CMD como administrador

#

![image](https://user-images.githubusercontent.com/96561825/173632053-bc1022d5-5bd5-48e1-9d4f-cbca00aa2e9c.png)


y probamos nuevamente, primero con un ping que conocemos ,

#

![image](https://user-images.githubusercontent.com/96561825/173632104-eba0fbaa-9031-4c4e-b2cd-8b50f9baf415.png)


Y después con el de la VM, como podemos ver en la siguiente imagen


![image](https://user-images.githubusercontent.com/96561825/173632132-2896d2b8-1d6e-4f2b-9b2f-e516110e486f.png)


#

Y el resultado fue


![image](https://user-images.githubusercontent.com/96561825/173632181-84ebe601-28fd-416a-a5f0-3f7451bae330.png)

Resultado negativo.

Seguimos investigando,  ampliaremos más adelante ya que esta última etapa del desafío nos está consumiendo demasiado tiempo en un error que no hemos podido resolver hasta ahora.

Hoy jueves temprano,  quisimos empezar en la mañana con pruebas para estar preparados y poder tener desplegada y lista una VM para la reunión con Gastón Baravalle,  para tratar de buscar soluciones al problema.  Lamentablemente eso no ocurrió,  recién a la tarde se nos habilito el patrocinio de parte de Microsoft gracias a la gentileza de Paola.

Jueves 22:30hs    -26.05.2022
PS: Quedo en volver a probar más adelante y rever donde está el error, por ahora culmino aquí para no seguir retrasándome. 

#
#
#
#
#
Seguimos en el [Día 43](day43.md)
























































