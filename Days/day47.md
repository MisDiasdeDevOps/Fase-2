# Creacion de VPC en Google Cloud para BootCamp DevOps Enginner


## Puede crear una red de VPC en modo automático o personalizado. 

Cuando se crean las redes en modo automático, estas automáticamente crean una subred en cada región de Google Cloud. Si opta por una red de VPC en modo personalizado, debe crear la red y, a continuación, las subredes que desee dentro de la región.

Puede generar las subredes al crear la red o agregarlas más adelante.

No se pueden crear instancias en una región en la que no hay ninguna subred definida.

Requisitos previos

Asegúrese de tener una cuenta de Google y la información de acceso o inicio de sesión para la consola de Google Cloud Platform (GCP).

Procedimiento

1. Inicie sesión en la consola de GCP.
2. Haga clic en Redes de VPC (VPC Networks).
3. Al realizar esta acción, aparece la página Redes de VPC (VPC Networks).
4. Haga clic en Crear red de VPC (Create VPC network).  Al realizar esta acción, aparece la página Crear una red de VPC (Create a VPC network).
5. En el cuadro de texto Nombre (Name), introduzca un nombre único para la red de VPC.
6. En Subredes (Subnets), elija Personalizado (Custom) o Automático (Automatic) en Modo de creación de subred (Subnet creation mode). Si elige Personalizado (Custom), especifique los siguientes parámetros de configuración para la subred en el área Nueva subred (New subnet):
    1. En el cuadro de texto Nombre (Name), introduzca un nombre único para la subred.
    2. En el menú desplegable Región (Region), seleccione una región para la subred.
    3. En el cuadro de texto Rango de direcciones IP (IP address range), introduzca el rango pertinente.
    4. A la hora de definir un rango de IP secundario para la subred, haga clic en Crear rango de IP secundario (Create secondary IP range).
    5. Acceso a Google privado (Private Google access): puede habilitar esta opción para la subred al crearla o editándola más adelante.
    6. Registros de flujo (Flow logs): puede habilitar los registros de flujo de VPC para la subred al crearla o editándola más adelante.
    7. Haga clic en Listo (Done).
7. Para agregar más subredes, haga clic en Agregar subred (Add subnet) y repita las indicaciones del paso 5. También puede agregar más subredes a la red después de crearla.
8. Elija el modo de enrutamiento dinámico para la red de VPC.
9. Haga clic en Crear (Create).

#

## Resultados : Al realizar esta acción, se crean la red y la subred de VPC.

#



#
#

![Screenshot_95](https://user-images.githubusercontent.com/96561825/173975513-2d18c3f2-e7a8-4641-b911-f9f7297b0d56.png)

#
#

![Screenshot_97](https://user-images.githubusercontent.com/96561825/173975595-6a117da0-7f0f-4ea8-9ce9-1059a761a530.png)

#
#

![Screenshot_98](https://user-images.githubusercontent.com/96561825/173975598-ad2cc85c-91c4-46b5-b0da-52a442dfde4b.png)

#
#

![Screenshot_99](https://user-images.githubusercontent.com/96561825/173975658-ff087c8a-bd31-47a5-8843-b913bc2cac50.png)

#
#

![Screenshot_101](https://user-images.githubusercontent.com/96561825/173975698-df057905-0ffa-4da8-a2ab-a270fa4d3e70.png)

#
#

![Screenshot_102](https://user-images.githubusercontent.com/96561825/173975731-d6d02ef7-6aec-4d19-a7c5-9ddb7086156b.png)

#
#

![Screenshot_103](https://user-images.githubusercontent.com/96561825/173975740-0a0755e1-af1b-4a0e-af25-1547710464d0.png)

#
#

![Screenshot_104](https://user-images.githubusercontent.com/96561825/173975749-bbd5f682-b511-40f0-b1bd-aa9c7fc3143e.png)

#
#

![Screenshot_105](https://user-images.githubusercontent.com/96561825/173975778-eb2d387d-16b8-432b-95a4-9cb56389f7fd.png)

#
#

![Screenshot_106](https://user-images.githubusercontent.com/96561825/173975791-22dd9ca8-f011-4024-bf40-f726be49524d.png)



#
#
#
#
#


Seguimos en el [Día 48](day48.md)



