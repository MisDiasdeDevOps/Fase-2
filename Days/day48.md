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







