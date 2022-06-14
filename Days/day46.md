
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


### VPC
Acceder a la consola de VPC y abrir "Create VPC".



