
## BootCamp DevOps Enginner

# Desafio VPC - SG -
#



En este desafio deberemos realizar esta actividad y entregar al tutor nuestra implementacion en un archivo zip junto con capturas de pantalla de la realizacion (Debe observarse la cuenta del alumno)
Introduccion al Desafio. 

El concepto de VPC en AWS representa lo que sería una VLAN en una red local, extendido a ruteo, subredes y más (una especie de VLAN con esteroides). 

Se trata de una red privada virtual donde podremos conectar nuestras instancias EC2, RDS y más. 

Una VPC es privada ya que sólo veremos tráfico asociado a nuestras instancias, y virtual en el sentido que estamos alojados en una nube pública compartida con miles de otros usuarios de AWS. Siempre
hay que tener en cuenta este punto, más allá de que sea una red privada, es virtual. 

Con lo cual la seguridad y confidencialidad del tráfico en nuestra VPC depende de la seguridad del proveedor de servicios en la nube (en este caso AWS). 

Por esta razón recomiendo siempre utilizar conexiones seguras (TLS) entre instancias, por más de que sea dentro de una red privada virtual.

#
#


### 1- VPC

Acceder a la consola de VPC y abrir "Create VPC".


#
![Screenshot_17](https://user-images.githubusercontent.com/96561825/173689032-1c82530d-6897-44bd-afce-fa8f0e6db794.png)
#

Ingresar un nombre ("vpc_desarrollo"), rango de red (10.50.0.0/16) y deshabilitar IPv6. 

Presionar "Create VPC".

Para comenzar se deja la tabla de ruteo y ACL de red con los valores por defecto.

#
#
![Screenshot_18](https://user-images.githubusercontent.com/96561825/173689311-bae4006b-8d53-4b2d-b351-2f6aad8beff1.png)

#
#

![Screenshot_20](https://user-images.githubusercontent.com/96561825/173689355-b624a0a4-b669-42df-b610-8e93b4729955.png)

#
#

![Screenshot_21](https://user-images.githubusercontent.com/96561825/173689397-8bf330dc-5851-493e-878b-cd2461fb6bbe.png)

#
#

![Screenshot_22](https://user-images.githubusercontent.com/96561825/173689439-0a188680-27d9-4152-80d3-6be10ea23266.png)

#
#

![Screenshot_24](https://user-images.githubusercontent.com/96561825/173689480-199a4205-9e28-41c3-b2a5-b5421c11888b.png)


#
#
#

### 2 - Subredes

Luego es necesario definir las subredes necesarias. Por ejemplo es conveniente definir subredes para correo, servidores de bases de datos (RDS) y DMZ para servidores web.

Acceder a "Subnets" desde el menú de la ***consola de VPC*** y presionar "Create subnet". 

Seleccionar la nueva VPC "vpc_desarrollo":
#

![Screenshot_25](https://user-images.githubusercontent.com/96561825/173689764-60ffb807-cbda-4cfe-9ca7-38378147e5f9.png)


#

![Screenshot_26](https://user-images.githubusercontent.com/96561825/173689781-3ab84018-95a4-4d14-9e58-6f08dab209e7.png)

#

De la misma forma se agregan las siguientes subredes:

● "Mail": 10.50.5.0/24

● "RDS-Subnet01-useast1a": 10.50.1.0/24

● "RDS-Subnet02-useast1b": 10.50.2.0/24

● "DMZ": 10.50.0.0/24



#
#
### 3 - Acceso a Internet


El siguiente paso consiste en definir un nuevo Internet Gateway para que las instancias en la subred "DMZ" tengan acceso a Internet y NAT (cuando se les asigne una IP pública o elástica).

Abrir "Internet Gateways" desde el menú de la consola de VPC y presionar "Create internet gateway".

Especificar un nombre ("igw-desarrollo") y crear.

Desde el Internet Gateway recién creado abrir "Actions > Attach to VPC". Seleccionar la VPC "vpc_desarrollo":

#
#

![Screenshot_27](https://user-images.githubusercontent.com/96561825/173690083-a2b2d9d3-bfa6-455f-9846-bd4aedb68067.png)


#
#

![Screenshot_28](https://user-images.githubusercontent.com/96561825/173690098-4bc54da0-224e-4961-8abf-ef705e961757.png)

#
#

![Screenshot_29](https://user-images.githubusercontent.com/96561825/173690105-39f4afb4-420b-44d7-b7a2-5848e91e4c38.png)

#
#

![Screenshot_30](https://user-images.githubusercontent.com/96561825/173690110-d10c6a7c-b81b-4ed0-8a1c-756612fa5488.png)


#
#

### 4 - Tablas de ruteo

El siguiente paso consiste en crear una nueva tabla de ruteo para dirigir el tráfico desde la "DMZ" hacia Internet a través del Internet Gateway creado en el paso anterior.

Acceder a "Route Tables" desde el menú de la consola de VPC y presionar "Create route table".

Seleccionar la VPC "vpc_desarrollo":

Crear la tabla de ruteo e inmediatamente acceder a la pestaña "Subnet Associations":
#

#
![Screenshot_33](https://user-images.githubusercontent.com/96561825/173690365-473632dc-20db-4e56-a514-9c28fd84b215.png)
#
#

Asociar a la subred "DMZ" de la VPC "vpc_desarrollo":

#

![Screenshot_34](https://user-images.githubusercontent.com/96561825/173690420-aa1bddd5-de1a-4cab-968a-5c38cf35e477.png)

#
#


Luego volver a la pestaña "Routes" y hacer clic en "Edit routes". 

Agregar la ruta hacia "0.0.0.0/0" (default gateway) a través del Internet Gateway creado anteriormente:

![Screenshot_37](https://user-images.githubusercontent.com/96561825/173690570-5262a340-7cd1-4d14-ae1d-cb28c2a3834d.png)

#
#

![Screenshot_38](https://user-images.githubusercontent.com/96561825/173690594-9f42a2d1-b697-45fb-a4d7-7e31d169cfea.png)



#
#
### 5 - Security Groups 

Por último es necesario crear al menos un grupo de seguridad para permitir el tráfico desde internet a la DMZ en la VPC "vpc_desarrollo". Acceder al menú "Security Groups" de la consola de VPC y presionar "Create security group".

Los "Security Groups" son esencialmente firewalls que se pueden asociar a diferentes instancias.

La configuración de seguridad de un grupo de seguridad depende de cada caso. 

Para un servidor Web típico es necesario abrir el acceso a los puertos 80 (HTTP) y 443 (HTTP/S) junto con el acceso por SSH.

EL grupo de seguridad luego se debe asociar a la instancia EC2 o RDS a la que se desea tener acceso.

La VPC "vpc_desarrollo" junto con sus subredes, security groups, tablas de ruteo y gateway está lista para funcionar.

Por último es necesario crear al menos un grupo de seguridad para permitir el tráfico desde internet a la DMZ en la VPC "vpc_desarrollo".



#
#
### 6 - Network access control list vs security group

### Security Group

- Opera “a nivel de la instancia”
- Soporta “solo allow rules” 
- Stateful: El tráfico de retorno depende de la “regla de entrada”
- Stateless: El tráfico de retorno debe ser definido
- AWS evalúa todas las reglas antes de decidir que trafico permitir
- Se aplica de manera selectiva a las instancias


#
#
### Network ACL

- Opera “a nivel de la subred”
- Soporta “allow y deny rules”
- Stateless: El tráfico de retorno debe ser definido explícitamente por reglas “allow”
- AWS procesa las reglas conforme a su numero
- Se aplica a todas las instancias asociadas a la subred




#
#
### 7 - Crea un grupo de seguridad para el balanceador de carga - Realizar Desafio Extra

## Introduce los parametros siguientes para el Grupo de Seguridad (Security group)


La configuración de seguridad de un grupo de seguridad depende de cada caso. Para un servidor Web típico es necesario abrir el acceso a los puertos 80 (HTTP) y 443 (HTTP/S) junto con el acceso por SSH. 


Nombre del grupo de Seguridad = LB-SG

Descripcion = VPC Grupo de seguridad del balanceador de carga


VPC = La VPC que has creado antes (ejemplo TargetVPC)


#
#

![Screenshot_47](https://user-images.githubusercontent.com/96561825/173694398-626470ec-8093-48be-a42b-ea393147046b.png)

#
#

![Screenshot_48](https://user-images.githubusercontent.com/96561825/173694403-4f932983-7459-4a2d-beef-8750ae9b4c65.png)
#
#

![Screenshot_49](https://user-images.githubusercontent.com/96561825/173694410-33d34d0e-1f10-44b0-8c70-23d4766ef97b.png)


#
#
#
#
#

Seguimos en el [Día 47](day47.md)

