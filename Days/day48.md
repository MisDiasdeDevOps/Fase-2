DESAFIO RDS en AWS - BootCamp DevOps Enginner



Amazon RDS es el servicio que facilita la configuración, funcionamiento y escalado de las BD relacionales en AWS. Con éste el BD Admin evita tener que administrar todos los
componentes relacionados con este tipo de BD (S.O. del servidor, almacenamiento, copia de seguridad, alta disponibilidad, …).



Antes de crear la instancia de la BD, se nos pide realizar una serie de acciones:

1. Crear un usuario IAM con permisos de administrador. Será con este usuario con el que realizemos el resto del tutorial. Amazon aconseja no usar nunca el usuario raíz,
salvo ocasiones puntuales, y guardar en lugar seguro sus credenciales.

2. La instancia de BD se creará en una VPC (Virtual Private Cloud). Por lo tanto, también será necesario definir las reglas de grupo de seguridad para tener acceso a
esta VPC, (que seguramente será del tipo EC2-VPC).

3. Aquí debe consultar la configuracion necesaria para el escenario elegido para el acceso a una instancia de BD situada en una VPC.

Para el caso que nos ocupa elegiremos el escenario con la instancia de BD en una VPC y una aplicación cliente a través de Internet.

![Uploading Screenshot_3.png…]()


![Screenshot_2](https://user-images.githubusercontent.com/96561825/173917310-7e8cb31a-16b2-48f0-b93b-ef3f94623df6.png)



![Screenshot_5](https://user-images.githubusercontent.com/96561825/173917354-2d8c8a39-62f9-4d0b-9e16-7e0c935dd4e0.png)


![Screenshot_6](https://user-images.githubusercontent.com/96561825/173917365-228d920f-e31a-4c96-a185-49577e069307.png)

![Screenshot_7](https://user-images.githubusercontent.com/96561825/173917379-ca48d7e6-3c6a-49be-b227-30e1d681eb6d.png)

![Screenshot_8](https://user-images.githubusercontent.com/96561825/173917393-f0e98841-ec9d-4494-b368-6b8b9526bb2e.png)


![Screenshot_9](https://user-images.githubusercontent.com/96561825/173917419-6a68b910-2700-422d-a3ca-a735d90f319e.png)

![Screenshot_10](https://user-images.githubusercontent.com/96561825/173917432-8bba95ff-eab0-4250-859a-1d429812736c.png)

![Screenshot_11](https://user-images.githubusercontent.com/96561825/173917441-3db61eb8-56cf-4a76-9211-1af23da3bca4.png)

![Screenshot_12](https://user-images.githubusercontent.com/96561825/173917479-87f18ec3-b10a-4f57-9946-05b7ae089ca0.png)


Crear la VPC
Ahora deberá crear una VPC para utilizarla con una instancia de base de datos, con la
configuración descrita en el punto anterior:
● Abra la consola de Amazon VPC en https://console.aws.amazon.com/vpc/.
● En la esquina superior derecha de la Consola de administración de AWS, elija la
región en la que desea crear la VPC.
● En la esquina superior izquierda, elija VPC Dashboard. Para comenzar a crear una
VPC, elija Launch VPC Wizard (Lanzar asistente de VPC).
a. En la página Step 1: Select a VPC Configuration, elija VPC with a Single Public Subnet y,
a continuación, elija Select.
b. En la página Step 2: VPC with Public Subnet, establezca estos valores:
● IPv4 CIDR block: 10.0.0.0/16
● IPv6 CIDR block: No IPv6 CIDR Block
● VPC name: tutorial-vpc
● Public subnet’s IPv4 CIDR: 10.0.0.0/24
● Availability Zone: No preference
● Public subnet name: Tutorial public
c. Cuando haya terminado, elija Create VPC.
Al ejecutar el wizard se crean los siguientes objetos:
● VPC
● Subnet
● Route Tables
● Internet Gateway
● Network ACL
● Security Group

![Screenshot_13](https://user-images.githubusercontent.com/96561825/173917761-caf38bf2-2402-4a98-b206-ecd6a90aa293.png)
![Screenshot_14](https://user-images.githubusercontent.com/96561825/173917776-33398f36-c04c-4e54-afb2-2ab1a17af9da.png)
![Screenshot_15](https://user-images.githubusercontent.com/96561825/173917786-7176a99a-730d-46be-a21b-f5cb243dc6e5.png)

![Screenshot_16](https://user-images.githubusercontent.com/96561825/173917792-6443b57e-cd5e-4f43-870b-6ec5cff26b0e.png)

![Screenshot_17](https://user-images.githubusercontent.com/96561825/173917802-3eac2cb4-2c02-4eca-b4ef-f9bce128a71b.png)

![Screenshot_18](https://user-images.githubusercontent.com/96561825/173917807-abc7850a-bd1f-4792-885d-8c5461c7a8ab.png)

![Screenshot_19](https://user-images.githubusercontent.com/96561825/173917810-fee2e905-d342-41aa-ba6f-38ca0ca011e9.png)

![Screenshot_20](https://user-images.githubusercontent.com/96561825/173917823-b3cbec7b-5990-43bd-8b60-2cde26a5c80b.png)

![Screenshot_21](https://user-images.githubusercontent.com/96561825/173917870-4f6ceb2b-10df-49d5-bafb-d8ee309f7935.png)


![Screenshot_22](https://user-images.githubusercontent.com/96561825/173917899-b5737a93-6901-4a4d-90d3-8167fcefd15a.png)


#
#
# Configurar el Security Group

Vaya al apartado Security Groups y seleccione el grupo que ha creado (asociado al nuevo VPC). 

Después seleccione Inbound rules del grupo.  

Le aparecerá con este tipo de configuración: 

Type Protoco
l
Port range Source
All traffic All All sg-d57b5896 (default)


La configuración por defecto sólo permite la conexión al VPC desde componentes que usen el mismo Security Group. Como queremos conectarnos a la BD desde cualquier punto de Internet deberemos modificar el valor de la propiedad Source: 

a. Edite Inbound rules.

b. En el campo Source seleccione la opción 0.0.0.0/0.

c. Pulse el botón Save rules.

Si quisiera limitar la conexión a la BD sólo a su equipo u otros de confianza, debería poner en el campo Source las IP de estos equipos. 

De esta forma la configuración quedaría asi: 

Type   MYSQL/Auror

Protoco  TCP

Port range 3306

Source    56.176.2.108/3

#

## 3 - Crear las subredes adicionales


Debe tener dos subredes privadas o dos subredes públicas disponibles para crear un grupo
de subredes de base de datos para que lo utilice una instancia de base de datos en una
VPC. Debido a que la instancia de base de datos de este tutorial es pública, debe añadir
una segunda subred pública a la VPC:


● Abra la consola de Amazon VPC en https://console.aws.amazon.com/vpc/.

● Para añadir la segunda subred privada a la VPC, elija VPC Dashboard (Panel VPC),seguido de Subnets (Subredes) y, por último, Create Subnet (Crear subred).
● En la página Create Subnet (Crear subred), defina estos valores:

● Name tag: Tutorial private 2

● VPC: elija la VPC que creó anteriormente, por ejemplo: vpc-identifier (10.0.0.0/16) - tutorial-vpc.

● Availability Zone: us-west-2b

Elija una zona de disponibilidad que sea distinta de la que eligió para la primera subred pública.

● IPv4 CIDR block: 10.0.2.0/24

● Cuando haya terminado, elija Create (Crear). A continuación, seleccione Close (Cerrar) en la página de confirmación.


a. Elija Panel de VPC, elija Subredes y, a continuación, elija la primera subred privada que creó para la VPC, Tutorial private 1. 

b. Debajo de la lista de subredes, elija la pestaña Route Table (Tabla de enrutamiento) y anote el valor de Route Table (Tabla de enrutamiento), por ejemplo: rtb-98b613fd.

c. En la lista de subredes, anule la selección de la primera subred privada. 

d. En la lista de subredes, elija la segunda subred privada Tutorial private 2 y elija la pestaña Tablas de ruteo. 

e. Si la tabla de ruteo actual no es la misma que la tabla de ruteo de la primera subred privada, seleccione Edit route table association (Editar asociación de tabla de ruteo). En  Route Table ID (ID de tabla de ruteo), elija la tabla de enrutamiento que anotó anteriormente, por ejemplo: rtb-98b613fd. A continuación, para guardar lo que ha seleccionado, elija Save (Guardar). 





![Screenshot_23](https://user-images.githubusercontent.com/96561825/173921756-b1c657cc-85b5-4a02-a4b2-c99094395029.png)


![Screenshot_24](https://user-images.githubusercontent.com/96561825/173921766-5eedf0a6-9311-467c-8426-280741f54542.png)

![Screenshot_25](https://user-images.githubusercontent.com/96561825/173921771-cbd30028-f591-4e88-8d9a-89f21664e4ea.png)


![Screenshot_26](https://user-images.githubusercontent.com/96561825/173921782-c39023d7-86b4-48c3-9c5a-7da86d05bc40.png)

![Screenshot_27](https://user-images.githubusercontent.com/96561825/173921795-5a89be3b-44ae-4e28-810f-8ecdbf86afe6.png)

![Screenshot_28](https://user-images.githubusercontent.com/96561825/173921803-6f192400-ce1b-47d5-ab15-af8771f2fe1d.png)

![Screenshot_29](https://user-images.githubusercontent.com/96561825/173921868-58344011-8e02-436b-aaf2-c5414dbdccf5.png)


![Screenshot_30](https://user-images.githubusercontent.com/96561825/173921878-bf27d59b-a06e-462d-9a96-1b57016c15b4.png)


#
#

## Crear un grupo de subredes de base de datos

 Un grupo de subredes de base de datos es una colección de subredes que se crean en una VPC y que después se asignan a las instancias de bases de datos. Un grupo de subredes de base de datos le permite especificar una VPC específica al crear instancias de bases de datos.
 
Para crear un grupo de subredes de base de datos 

● Abra la consola de Amazon RDS en https://console.aws.amazon.com/rds/.  Asegúrese de conectarse a la consola de Amazon RDS, no a la consola de Amazon VPC.

● En el panel de navegación, elija Subnet groups.

● Elija Create DB Subnet Group.
 
● En la página Create DB subnet group (Crear grupo de subredes de base de datos), establezca estos valores en Subnet group details (Detalles del grupo de subredes):

● Name: tutorial-db-subnet-group

● Description: Tutorial DB Subnet Group

● VPC: tutorial-vpc (vpc-identifier)

● En la sección Agregar subredes elija las Zonas de disponibilidad y Subredes.

En este tutorial, elija us-west-2a y us-west-2b para las Zonas de disponibilidad. A continuación, elija todas las subredes para Subredes.

Si ha habilitado una zona local, puede elegir un grupo de zonas de disponibilidad en la página Create DB subnet group (Crear grupo de subredes de base de datos). 

En este caso, elija Availability Zone group (Grupo de zonas de disponibilidad), Availability Zones (Zonas de disponibilidad)y Subnets (Subredes).

● Seleccione Create. El nuevo grupo de subredes de base de datos aparece en la lista de grupos de subredes de base de datos de la consola de RDS.


![Screenshot_34](https://user-images.githubusercontent.com/96561825/173922565-de2289a5-47bf-414e-a62f-234a318fe551.png)

![Screenshot_35](https://user-images.githubusercontent.com/96561825/173922571-93fb2b01-69a7-41b2-a18d-dee719c7425c.png)


![Screenshot_36](https://user-images.githubusercontent.com/96561825/173922579-e74d8a13-2f88-4261-909e-429cbfed1878.png)





#
#
# 5 - Crear la instancia de base de datos en la VPC

1. Abra la consola de Amazon RDS en https://console.aws.amazon.com/rds/. 
2. Seleccionamos la región en la que queremos crear la instancia de BD (esquina superior derecha). Esta región deberá ser la misma en la que se creó la VPC.
3. Seleccione Databases. 
4. Pulsamos el botón Create database. 
5. Usaremos la opción Standard Create, que permite seleccionar la VPC, a demás de configuraciones como disponibilidad, seguridad, copias de seguridad y mantenimiento. La opción Easy Create siempre utilizará la VPC por defecto, por lo que en nuestro caso no nos sirve. 
6. Engine Type: Seleccionamos el motor de BD que vayamos a utilizar en esta instancia. En nuestro caso MariaDB. Si quisiera instalar una instancia de BD MySql debería seleccionar ésta en vez de MariaDB. 
7. DB instance size: Seleccionamos Free tier para economizar gastos. 
8. Indicamos un nombre para la instancia de BD y el nombre del usuario administrador de la BD. 
9. Pulsamos en Auto generate a password. Cuando creemos la BD nos mostrará en ese único momento la contraseña, que deberemos guardar. Si desea indicar
manualmente una contraseña desmarque esta opción.
10. Las siguientes opciones las dejaremos como aparecen por defecto. 
11. En Connectivity seleccionamos la VPC que hemos creado en el anterior apartado.

Y Desplegamos Additional connectivity configuration.

12. Seleccionamos el Subnet group que hemos creado anteriormente
13. En Public access seleccionamos Yes para que podamos acceder a la BD desde cualquier equipo en Internet.
14. Las siguientes opciones las dejaremos como aparecen por defecto.
15. Pulsamos el botón Create database al final de la página.
16. Pulsamos el botón View credential details. Se abrirá una ventana para ver:
● La contraseña creada para el usuario administrador.
● La dirección (Endpoint) de la instancia a la que nos conectaremos con nuestro cliente.


![Screenshot_37](https://user-images.githubusercontent.com/96561825/173923200-59dea955-1837-436a-a566-0c0fccb87dd8.png)

![Screenshot_38](https://user-images.githubusercontent.com/96561825/173923213-f86bb7c4-7388-4f5d-bee3-92a2f07185fc.png)

![Screenshot_39](https://user-images.githubusercontent.com/96561825/173923222-5060e086-df1e-42b6-b035-bec830dd5f2e.png)

![Screenshot_40](https://user-images.githubusercontent.com/96561825/173923225-e4d7a6b4-7bc9-4c90-b1c6-0f0db955c8b2.png)

![Screenshot_41](https://user-images.githubusercontent.com/96561825/173923231-4743d178-e244-49c2-ba11-ee6ea13e5221.png)



#
#
# Comprobar el acceso a la instancia


Una vez creada la instancia, podremos comprobar que accedemos a ella mediante
cualquier cliente instalado en nuestra máquina. Por ejemplo mediante el comando mariadb
de la consola:
Suponemos que el Endpoint que nos ha creado es
mariadbinstancia.skdimeitllwst.us-west-1.rds.amazonaws.com
$ mariadb -h mariadbinstancia.skdimeitllwst.us-west-1.rds.amazonaws.com -u username -p
password
Welcome to the MariaDB monitor. Commands end with ; or \g.
Your MariaDB connection id is 60
Server version: 10.1.34-MariaDB MariaDB Server
Copyright (c) 2000, 2018, Oracle, MariaDB Corporation Ab and others.
Type 'help;' or '\h' for help. Type '\c' to clear the current input statement.
MariaDB [(none)]> show databases;
+--------------------+
| Database |
+--------------------+
| information_schema |
| innodb |
| mysql |
| performance_schema |
+--------------------+
4 rows in set (0.05 sec)
MariaDB [(none)]>


![Screenshot_42](https://user-images.githubusercontent.com/96561825/173923541-caa87e96-9933-48ab-b3d3-5f00f5e68686.png)


![Screenshot_43](https://user-images.githubusercontent.com/96561825/173923544-3fe15647-f2ec-4f1a-a498-baee560c2db4.png)



![Screenshot_44](https://user-images.githubusercontent.com/96561825/173923547-c08c7394-4954-49f8-ba70-54b5f7d327ed.png)

![Screenshot_45](https://user-images.githubusercontent.com/96561825/173923551-cda568d1-d8ea-4471-b183-af46ba56bd61.png)

![Screenshot_46](https://user-images.githubusercontent.com/96561825/173923554-c92a5c75-7e45-465d-8848-4ed0b91907b9.png)

![Screenshot_46](https://user-images.githubusercontent.com/96561825/173923565-61e39872-f79f-4ca6-a5ef-6915381c0a1b.png)

![Screenshot_47](https://user-images.githubusercontent.com/96561825/173923573-54a56294-d2c4-431a-9013-49d3f093eca5.png)

![Screenshot_48](https://user-images.githubusercontent.com/96561825/173923598-6602bc4e-fa82-4b7f-91e6-f13c770a8bbe.png)

![Screenshot_49](https://user-images.githubusercontent.com/96561825/173923607-acde2323-26d4-4c30-aa8a-254f3cb7bc62.png)

![Screenshot_50](https://user-images.githubusercontent.com/96561825/173923617-4b5b6450-476e-4753-aea6-95f4de81a7a6.png)

![Screenshot_51](https://user-images.githubusercontent.com/96561825/173923626-96b18cb6-0bf9-4f91-bdfe-2f649e2cd942.png)

#![Screenshot_134](https://user-images.githubusercontent.com/96561825/173923642-e50e812d-d7ba-4afe-ad7a-ee0b9db26665.png)



#
## Posibles problemas


### Route Tables

Desde AWS VPC, vaya a Route Tables y compruebe que la Route table asociada a la VPC de la BD tiene asociadas las dos Subnets creadas, y en Main indica Yes.
Otros errores. Si ha tenido otros problemas para conectarse a la instancia, en esta página puede consultar algunas soluciones propuestas por AWS.

### Mejorar la seguridad
En este tutorial hemos sugerido el uso del Security Group como firewall para limitar la conexión a la IP de nuestro equipo. Sin embargo, si la BD sólo necesitara estar expuesta a otro componente dentro de AWS (p.e. un servidor HTTP), es posible aumentar su seguridad utilizando una subnet privada y un servidor SSH dentro de la misma VPC para acceder a la
BD a través de éste.

#
#
#
#
#
Seguimos en el [Día 49](day49.md)
