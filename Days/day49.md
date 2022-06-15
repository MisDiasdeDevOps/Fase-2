


# Desafio BootCamp DevOps - 
# Creacion de Clusters con Google Kubernetes Engine de GCP
#


Para los desarrolladores con una experiencia mínima en DevOps, la curva de aprendizaje de Kubernetes y de los numerosos proveedores de alojamiento en la nube puede ser empinada. La documentación de Google Cloud Platform proporciona una explicación clara y detallada de
la plataforma y de cómo comenzar, pero el nivel de detalle puede resultar abrumador para los desarrolladores que no están familiarizados con las arquitecturas nativas de la nube.


## 1 - Como Comenzar
#


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
## 2 - Crea el clúster
#

Una vez que se haya registrado, se le entregará un Proyecto.
#
#
![Screenshot_3](https://user-images.githubusercontent.com/96561825/173929444-3e0b7a41-ad8e-49ef-a7c8-507a818421ba.png)

#
#

![Screenshot_4](https://user-images.githubusercontent.com/96561825/173929452-9c435124-1f22-412b-9e61-427798fe9095.png)
#
#

![Screenshot_5](https://user-images.githubusercontent.com/96561825/173929526-8e11dc09-4a5d-48b8-a74f-38bbef731552.png)

#
#
## 3 - Así se puede visualizar el panel una vez creado el Proyecto

#
![Screenshot_6](https://user-images.githubusercontent.com/96561825/173929612-e1a5de78-1eb2-40b8-b1cb-6728d3b2ae9f.png)
#
#

![Screenshot_7](https://user-images.githubusercontent.com/96561825/173929775-2f49c28f-f4f2-4f1e-b7fc-424df4feacb3.png)

#
#
## 4 - Creando una Cuenta de Servicio
#
#

![Screenshot_8](https://user-images.githubusercontent.com/96561825/173929789-d126edd2-bd78-4795-b659-9009ceaae6da.png)
#
#

La cuenta de servicio proporciona acceso a sus herramientas para crear y actualizar recursos en su clúster.

HAGA CLIC EN EL MENÚ DE LA CONSOLA EN LA PARTE SUPERIOR IZQUIERDA, RESALTE IAM Y ADMINISTRADOR Y HAGA CLIC EN CUENTAS DE SERVICIO:

#
#
![Screenshot_9](https://user-images.githubusercontent.com/96561825/173929867-ef97c597-3cb0-4513-864c-b4e827c7ea7d.png)
#
#


## 5 - Haga clic en Crear cuenta de servicio en la parte superior de la página.

#
#
![Screenshot_10](https://user-images.githubusercontent.com/96561825/173929957-a055ed8b-bfd3-45e1-94ca-fd16ce692bc6.png)
#
#

Ingrese un nombre para su cuenta de servicio y haga clic en Crear.
#
#

![Screenshot_11](https://user-images.githubusercontent.com/96561825/173929978-10c39a97-79f1-48bb-a24a-6b888dc347f1.png)

#
#

A continuación, debe definir los permisos para la cuenta de servicio. 

Haga clic en el campo desplegable, ingrese Administrador de Kubernetes Engine y haga clic en la función cuando aparezca:

Luego, Al seleccionar los permisos de IAM

- ADMINISTRADOR DE CLUSTERES DE KUBERNETES ENGINE

- ADMINISTRADOR DE KUBERNETES ENGINE


#
#
![Screenshot_13](https://user-images.githubusercontent.com/96561825/173930202-b5e57169-75d0-4251-97f9-e120f3850303.png)
#
#



Concedemos a la cuenta que se crea una vez que la nombramos y que esta asociada al nombre de nuestro proyecto 

Ya podemos hacer click en  LISTO

#
#
![Screenshot_15](https://user-images.githubusercontent.com/96561825/173930277-625fe3f5-6d94-415d-a233-31ea7625f53f.png)
#
#
### Ahora debemos crear la Clave de la Cuenta de Servicio y Almacenarla en formato JSON, en nuestro equipo
#
#

![Screenshot_16](https://user-images.githubusercontent.com/96561825/173930291-9c094180-f810-4586-aeae-5b1a68213322.png)
#
#

![Screenshot_17](https://user-images.githubusercontent.com/96561825/173930337-289a20af-f243-4309-acd6-5672891ac55c.png)

#
#

![Screenshot_18](https://user-images.githubusercontent.com/96561825/173930413-6ef60f4a-3db4-4f6f-9741-44a924eaeedf.png)

#
#

![Screenshot_19](https://user-images.githubusercontent.com/96561825/173930423-e38be0b2-65f1-4c57-9c54-4124e568040b.png)

#
#

Elegimos el formato recomendado : JSON

#
#
![Screenshot_20](https://user-images.githubusercontent.com/96561825/173930446-3ce9998f-5729-48e7-9bb2-b9f31178e4b1.png)
#
#


La almacenamos en un lugar seguro

#


# 6 - Comenzar con GKE
#

Una vez que se haya registrado, se le entregará un Proyecto. Aquí es donde crea todos sus recursos de GCP.+

Ahora, haga clic en el menú de la consola en la parte superior izquierda, resalte Kubernetes Engine y haga clic en Clústeres:


#
#
![Screenshot_22](https://user-images.githubusercontent.com/96561825/173936328-ed3deeca-660e-45f6-a0cc-cfb570ef6576.png)
#
#

![Screenshot_23](https://user-images.githubusercontent.com/96561825/173936365-e199c419-ad8d-4f37-9d6b-e29bcdae1be9.png)
#
#


## 7 - Los clusteres Zonales en GKE son gratuitos (dentro del Free Tier)

Ahora, haga clic en el botón Crear clúster.

#
#
![Screenshot_24](https://user-images.githubusercontent.com/96561825/173936472-fc5f395b-197b-41cd-8fd2-cbb692e8f3e1.png)
#
#


En este punto, verá una larga lista de plantillas de clúster y opciones de clúster para elegir.

Deje seleccionada la opción Clúster estándar e ingrese un nuevo nombre para el clúster en el campo Nombre.

En la prueba gratuita, solo se le permite crear un clúster zonal, así que deje esta opción seleccionada.

ELIJA UNA ZONA QUE ESTÉ UBICADA CERCA DE USTED.

La versión maestra define qué versión de Kubernetes utilizará su clúster.

Hay muchas opciones para elegir, y puede dejarlo configurado en la opción predeterminada.



## 8 Una vez que la API se habilita, simplemente podremos clear clústeres de GKE
 
### YA PODEMOS COMENZAR A CREAR CLUSTERES ZONALES CON LA CAPA GRATUITA DE GKE EN GCP


![Screenshot_25](https://user-images.githubusercontent.com/96561825/173937097-4b61a29b-cb79-4fd3-9fee-3d8e9cc4f28f.png)

#

## 9 - CREANDO CLUSTERS

### LA SIGUIENTE SECCIÓN LE PERMITE CONFIGURAR EL GRUPO DE NODOS PREDETERMINADO PARA SU CLÚSTER. ESTE ES EL GRUPO DE MÁQUINAS QUE GCP DEDICA A EJECUTAR SU CLÚSTER Y SUS RECURSOS. 

#
#
![Screenshot_26](https://user-images.githubusercontent.com/96561825/173937337-8c86d0bb-5439-47e8-947b-18a5ad94d9f9.png)
#
#

Y SELECCIONAR LA ZONA MAS CERCANA A NUESTRA LOCALIDAD ( SI ESTAS EN SUD AMERICA, SOUTH AMERICA ES LA INDICADA) 

LA VERSIÓN MAESTRA (EL NODO MAESTRO)


## 10 - LA VERSIÓN PREDETERMINADA NOS SERÁ ÚTIL ¡

SELECCIONANDO LOS NODOS , NOMBRANDOLOS Y SELECCIONANDO LA CANTIDAD DE NODOS

#
#
![Screenshot_28](https://user-images.githubusercontent.com/96561825/173938990-f454d81e-ea57-4ecf-ae0a-95fe0c301276.png)
#
#


## 11 - Para el ejemplo, he nombrado a los nodos “ educacionitpool” con 2 nodos! (Solo 2 recursos en el cluster)

#
#
![Screenshot_29](https://user-images.githubusercontent.com/96561825/173939118-f67f5e55-8bbb-4699-9a39-46cc82d96890.png)
#
#

En la configuración del Pool de nodos “Educacionitpool” he seleccionado en “Nodos” el sistema operativo de los Nodos (las maquinas virtuales en nuestro cluster” y he elegido Ubuntu. 

Luego para no realizar grandes costos, he seleccionado como tipo de maquina, N1-Standard-1

#
#
![Screenshot_29](https://user-images.githubusercontent.com/96561825/173939380-a16a74bd-ea26-48d3-a43d-6d4d30e31861.png)
#
#

## 12 -Seguridad

En materia de Seguridad he habilitado la cuenta de servicio kuberadmin (Creada al principio) y Habilite la

“Monitorización de Integridad” para monitorear la integridad de los Nodos del Cluster.




#
#
![Screenshot_30](https://user-images.githubusercontent.com/96561825/173939674-d9707cdb-d555-4bd7-b60f-9825bfdff611.png)
#
#

ANTES DE CREAR EL CLUSTER EN GKE, PUEDO VER UNA VERSIÓN PANORÁMICA DE COMO SE CREAR MI CLUSTER.
#
#

![Screenshot_31](https://user-images.githubusercontent.com/96561825/173939727-bcf3320f-18d9-42a6-85c0-3e300ee90f66.png)
#
#

## 13 - Ahora ya podemos seleccionar “Crear” y…Creando!!!
#

GCP TARDARÁ ALGÚN TIEMPO EN ACTIVAR SU CLÚSTER (POR LO GENERAL, AL MENOS CINCO MINUTOS). GCP LE ENVIARÁ UNA NOTIFICACIÓN EN LA IU CUANDO SU CLÚSTER ESTÉ LISTO.
NO LO OLVIDE: SI EN ALGÚN MOMENTO DECIDE QUE NO NECESITA SU CLÚSTER, DEBE ELIMINARLO ANTES DE QUE SE AGOTE SUS CRÉDITOS GRATUITOS.

#
#

![Screenshot_32](https://user-images.githubusercontent.com/96561825/173939792-d8951283-3cdf-4f64-a172-975f3a0cd585.png)

#
#




## 14 -  Ha Finalizado!


#
#

![Screenshot_33](https://user-images.githubusercontent.com/96561825/173939849-0d473965-d90f-4e6e-b42e-680673135f1b.png)

#
#

![Screenshot_34](https://user-images.githubusercontent.com/96561825/173939870-e15d4a6a-65a3-40e5-b3c9-0530a7b7db14.png)

#
#

Podemos confirmar en GCP, en la sección Compute Engine, que los nodos como maquinas virtuales, han sido creados y  enlazados al cluster

#
#

![Screenshot_35](https://user-images.githubusercontent.com/96561825/173940834-f3ff14f9-2f43-4d8f-a492-c59ecf2458b5.png)

#
#



## 15 - Nuestros 2 nodos funcionando y a los cuales podemos acceder via SSH (Siendo ambos Ubuntu 18 LTS)


#
#

![Screenshot_37](https://user-images.githubusercontent.com/96561825/173939935-ad09d637-26c4-4378-9cfa-eda33ee22516.png)

#
#








#

# ADMINISTRANDO LOS NODOS

#
#

![Screenshot_38](https://user-images.githubusercontent.com/96561825/173940105-220339a9-952a-49b7-9dfc-c1e87532aba1.png)

#
#

## 16 - PODEMOS NAVEGAR EN LOS NODOS PARA HACER DEPLOYMENTS O MODIFICACIONES EN ELLOS MEDIANTE EL NAVEGADOR!

SELECCIONANDO LA INSTANCIA EN COMPUTE ENGINE Y HACIENDO CLICK EN “CONECTAR” SSH – ABRIR LA VENTANA DEL NAVEGADOR.

#
#

![Screenshot_39](https://user-images.githubusercontent.com/96561825/173940146-91bd1aa7-c9c2-442e-b46e-63191ad31bee.png)

#
#


![Screenshot_40](https://user-images.githubusercontent.com/96561825/173940155-189da5ce-3d0d-44a6-9874-ed83014f73ca.png)

#
#

SI EJECUTAMOS EL COMANDO

LSB_RELEASE -A

Podremos saber la versión de el OS de nuestro nodo


#
#
![Screenshot_41](https://user-images.githubusercontent.com/96561825/173940210-6138a9b3-2cfb-4154-b64e-7b1ec124d5ed.png)
#
#

![Screenshot_42](https://user-images.githubusercontent.com/96561825/173940226-493d0eab-be3b-4f24-b1dc-c86714b83a3c.png)
#
#

## 17 - Y podremos ver la información de su creación en Kubernetes Engine 


Hemos creado rápidamente nuestro Cluster de Manera Gratuita!

NO TE OLVIDES DE ELIMINARLO!


#
#

![Screenshot_43](https://user-images.githubusercontent.com/96561825/173940248-925a951e-137c-46d0-9c68-29f8fd3972f7.png)

#
#

![Screenshot_44](https://user-images.githubusercontent.com/96561825/173940255-39850e6c-5b2b-4016-bb56-20746ec11ed4.png)

#
#

![Screenshot_45](https://user-images.githubusercontent.com/96561825/173940264-1160c342-a726-4e03-960b-1977fb659204.png)




#
#
#
#
#







