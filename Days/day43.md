
## BootCamp DevOps Engineer	

#  Sitio Estático  en AWS 

### 04   Desafío 2 AWS – Semana 1 – Sitio Estático en AWS - Profesores Gino Rojo – Gastón Baravalle


#
#

Accedemos a la consola de AWS y nos identificamos.

Dentro de la consola buscamos el recurso S3.

![image](https://user-images.githubusercontent.com/96561825/173635168-486177e2-4867-449b-bb16-cb9e72c4b73b.png)

#
Creamos un nuevo bucket.

![image](https://user-images.githubusercontent.com/96561825/173635420-6778113e-8f87-4d7f-b84b-e5a967300cb5.png)

#

Le damos un nombre único y dejamos la región por defecto.

![image](https://user-images.githubusercontent.com/96561825/173635467-ab0ebb39-d068-4c9b-95a2-83ece90bdf85.png)

#

Un sitio web es accesible por cualquier usuario por lo que debemos permitir el acceso público a nuestro bucket.

Desmarcamos el bloqueo del acceso público y podemos dejar el resto de la configuración por defecto.

![image](https://user-images.githubusercontent.com/96561825/173635548-d1d9e179-6f3e-4a1e-b921-c144fab04d46.png)

#

Listo, esta creado

![image](https://user-images.githubusercontent.com/96561825/173635623-0c8f646b-8908-483d-b221-f045eb3a4f5f.png)

#

Veremos esta pantalla al estar listo

![image](https://user-images.githubusercontent.com/96561825/173635668-590cd30c-0c8b-4d61-8758-917dad635180.png)


#

Los bucket no tienen herencia, por lo que permitir el acceso público al bucket no implica que sus objetos tengan acceso público. 

Debemos crear una política, que permita el acceso a los objetos, y asociarlo al bucket. 

![image](https://user-images.githubusercontent.com/96561825/173635726-e073049c-fb8a-4918-a850-bc0cf1331f4b.png)


#

Para ello, en la sección Permisos buscamos el apartado Política de bucket y le damos a Editar

![image](https://user-images.githubusercontent.com/96561825/173635769-f658df33-4342-42a7-ab5a-8ef4dd51c925.png)

#

Copiamos el ARN del bucket (nos servirá para el siguiente paso) y le damos Generador de políticas.

![image](https://user-images.githubusercontent.com/96561825/173635804-4c942706-4908-4945-8638-5499a7169014.png)

#
Aquí se nos abrirá la siguiente pantalla

![image](https://user-images.githubusercontent.com/96561825/173635852-e7a8bdef-a301-4bf2-be0d-4a8ae6675897.png)


#
Como tipo de política seleccionamos S3 Bucket Policy.

![image](https://user-images.githubusercontent.com/96561825/173635896-c2c5de52-3c08-4b96-b6f5-19701c84ea3c.png)


#

En Statement, rellenamos el campo Principal con un asterisco y seleccionamos GetObject como action.

![image](https://user-images.githubusercontent.com/96561825/173635954-f0356cfc-265a-44b4-aeb1-4429fd1bec30.png)

Le damos a Add Statement,

#

 y después de ver el resumen del statement le damos a Generate Policy.
 
 ![image](https://user-images.githubusercontent.com/96561825/173636036-1065c66e-9a07-4c77-b3d6-69035fb70be8.png)

#

Se nos abrirá una ventana con el JSON de la política, la copiamos y volvemos a la pantalla anterior 

![image](https://user-images.githubusercontent.com/96561825/173636087-8ad02103-d6ae-4c14-bd8d-eb2e46c76332.png)

#

Pegamos el JSON de la política y lo guardamos.  (ver HOJA 10 )

![image](https://user-images.githubusercontent.com/96561825/173636121-ce6e2c1d-afe7-4557-8c13-d8748610c6f4.png)


#

Al finalizar veremos la confirmación


![image](https://user-images.githubusercontent.com/96561825/173636193-fbd0d9c0-bcd8-4017-ab8b-5ae14c270c3a.png)

#

Una vez configurado los permisos, procedemos a subir nuestros ficheros.

Podemos arrastrar los ficheros a la zona del bucket o usar el botón cargar y seleccionar los ficheros.

Le damos a cargar y volvemos al bucket.

![image](https://user-images.githubusercontent.com/96561825/173636226-9a32c865-c016-4374-ba72-399eb317ff5f.png)



#

Una vez configurado los permisos, procedemos a subir nuestros ficheros. 

Podemos arrastrar los ficheros a la zona del bucket o usar el botón cargar y seleccionar los ficheros. Le damos a cargar y volvemos al bucket.

![image](https://user-images.githubusercontent.com/96561825/173636283-e253c512-eaf6-45f5-b975-146c5ef4a2c9.png)

#
Para alojar nuestro sitio web deberemos buscar en la sección Propiedades el apartado Alojamiento de sitios web estáticos y darle a Editar.


![image](https://user-images.githubusercontent.com/96561825/173636329-845ccdf0-7c1a-421e-842c-f59a4196fc1f.png)

#
Habilitamos el alojamiento, indicamos el nombre del documento que queremos que funcione como índice, y también indicamos el nombre de la página de error si la tuviéramos en el bucket.

![image](https://user-images.githubusercontent.com/96561825/173636379-7de02ff9-9e3b-4534-9be1-a696895ad519.png)


#

Guardamos los cambios y si volvemos a la sección Propiedades en el apartado Alojamiento veremos la dirección de nuestro sitio web en ACCION.

![image](https://user-images.githubusercontent.com/96561825/173636408-1b4f3252-6010-4a52-90ff-f56e415021b1.png)

#

Si queremos mostrar una página en caso de producirse un error indicaríamos el nombre del fichero del bucket en Documento de error.  

En este caso use la imagen de Netflix para gestionar el código de ERROR .

![image](https://user-images.githubusercontent.com/96561825/173636479-9ffb49eb-5e3b-4e26-9421-d14b609e5d33.png)


#
#



Para concluir eliminamos lo creado

![image](https://user-images.githubusercontent.com/96561825/173636536-4d88e5fa-2d6b-4fa4-8b7f-58bf90a46436.png)

#

Antes que nada vaciamos el BUCKET

![image](https://user-images.githubusercontent.com/96561825/173636582-7cbd0ccd-ed51-4b00-9aef-9bdec56681a4.png)

#

Y lo eliminamos

![image](https://user-images.githubusercontent.com/96561825/173636617-0719ed5b-a99e-4d15-abe3-df40b4881ce9.png)

#

Pantalla de confirmación de eliminación

![image](https://user-images.githubusercontent.com/96561825/173636641-c8577379-1d8a-4bae-b40e-26357b1e7e16.png)

#
#
#
#
#
Seguimos en el [Día 44](day44.md)
