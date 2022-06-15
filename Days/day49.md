


# Desafio BootCamp DevOps - 
# Creacion de Clusters con Google Kubernetes Engine de GCP


Para los desarrolladores con una experiencia mínima en DevOps, la curva de aprendizaje de Kubernetes y de los numerosos proveedores de alojamiento en la nube puede ser empinada. La documentación de Google Cloud Platform proporciona una explicación clara y detallada de
la plataforma y de cómo comenzar, pero el nivel de detalle puede resultar abrumador para los desarrolladores que no están familiarizados con las arquitecturas nativas de la nube.


## 1 - Como Comenzar?

En esta guía, le mostraré cómo comenzar rápidamente con un clúster de Kubernetes básico utilizando la interfaz de usuario de GCP. En la última sección, puede configurar opcionalmente su clúster para que
pueda implementar aplicaciones desde fuera de GCP. Al final, tendrá un clúster de Kubernetes listo para admitir una aplicación básica en contenedores.

Comenzemos!

Lo primero es lo primero: continúe y regístrese para obtener una cuenta de GCP si aún no lo ha hecho.

Google ofrece una prueba gratuita de 12 meses de la plataforma que incluye 300 € en créditos.

Esto ofrece mucho espacio para crear clústeres simples e implementar aplicaciones. 

Sin embargo, las limitaciones de recursos en la versión de prueba gratuita le impedirán implementar algo demasiado
complejo.

#
#
## 2. Crea el clúster

Una vez que se haya registrado, se le entregará un Proyecto.

#
![Screenshot_3](https://user-images.githubusercontent.com/96561825/173929444-3e0b7a41-ad8e-49ef-a7c8-507a818421ba.png)
#
![Screenshot_4](https://user-images.githubusercontent.com/96561825/173929452-9c435124-1f22-412b-9e61-427798fe9095.png)
#
![Screenshot_5](https://user-images.githubusercontent.com/96561825/173929526-8e11dc09-4a5d-48b8-a74f-38bbef731552.png)

#
#
Así se puede visualizar el panel una vez creado el Proyecto


![Screenshot_6](https://user-images.githubusercontent.com/96561825/173929612-e1a5de78-1eb2-40b8-b1cb-6728d3b2ae9f.png)
![Screenshot_7](https://user-images.githubusercontent.com/96561825/173929775-2f49c28f-f4f2-4f1e-b7fc-424df4feacb3.png)

#
#
Creando una Cuenta de Servicio

![Screenshot_8](https://user-images.githubusercontent.com/96561825/173929789-d126edd2-bd78-4795-b659-9009ceaae6da.png)

La cuenta de servicio proporciona acceso a sus herramientas para crear y actualizar recursos en su
clúster.

HAGA CLIC EN EL MENÚ DE LA CONSOLA EN LA PARTE SUPERIOR IZQUIERDA, RESALTE IAM Y ADMINISTRADOR Y HAGA CLIC EN CUENTAS DE
SERVICIO:


![Screenshot_9](https://user-images.githubusercontent.com/96561825/173929867-ef97c597-3cb0-4513-864c-b4e827c7ea7d.png)

#


Haga clic en Crear cuenta de servicio en la parte superior de la página.

#

![Screenshot_10](https://user-images.githubusercontent.com/96561825/173929957-a055ed8b-bfd3-45e1-94ca-fd16ce692bc6.png)
#
Ingrese un nombre para su cuenta de servicio y haga clic en Crear.
#
![Screenshot_11](https://user-images.githubusercontent.com/96561825/173929978-10c39a97-79f1-48bb-a24a-6b888dc347f1.png)
#

A continuación, debe definir los permisos para la cuenta de servicio. 

Haga clic en el campo desplegable, ingrese Administrador de Kubernetes Engine y haga clic en la función cuando aparezca:

Luego, Al seleccionar los permisos de IAM

- ADMINISTRADOR DE CLUSTERES DE KUBERNETES ENGINE

- ADMINISTRADOR DE KUBERNETES ENGINE


![Screenshot_13](https://user-images.githubusercontent.com/96561825/173930202-b5e57169-75d0-4251-97f9-e120f3850303.png)


#

## Podemos dar click en listo


![Screenshot_15](https://user-images.githubusercontent.com/96561825/173930277-625fe3f5-6d94-415d-a233-31ea7625f53f.png)


![Screenshot_16](https://user-images.githubusercontent.com/96561825/173930291-9c094180-f810-4586-aeae-5b1a68213322.png)

![Screenshot_17](https://user-images.githubusercontent.com/96561825/173930337-289a20af-f243-4309-acd6-5672891ac55c.png)

![Screenshot_18](https://user-images.githubusercontent.com/96561825/173930413-6ef60f4a-3db4-4f6f-9741-44a924eaeedf.png)
![Screenshot_19](https://user-images.githubusercontent.com/96561825/173930423-e38be0b2-65f1-4c57-9c54-4124e568040b.png)

![Screenshot_20](https://user-images.githubusercontent.com/96561825/173930446-3ce9998f-5729-48e7-9bb2-b9f31178e4b1.png)


Concedemos a la cuenta que se crea una vez que la nombramos y que esta asociada al nombre de nuestro proyecto 

Ya podemos hacer click en

LISTO

