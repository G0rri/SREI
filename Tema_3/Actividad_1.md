## Creación de VPC

Lo primero será crear una VPC (Virtual Private Cloud), para ello buscamos VPC y le damos a donde pone crear.

![image](https://github.com/user-attachments/assets/98199e9b-89bc-4393-8c51-62b3a33e8249)

A continuación empezamos con la creación de la VPC y más. Le asignamos un nombre, y que el bloque del CIDR IPv4 sea 10.2.0.0/16. Por el resto seguimos como en la imagen.

![image](https://github.com/user-attachments/assets/c61bc710-b12f-4bb5-958e-ecb8d33aceb1)

Ahora debemos especificar en cada subred el tamaño e IP que queremos, para el resto lo dejamos como en la imagen.

![image](https://github.com/user-attachments/assets/9a7e380e-1716-4bd5-9228-bc0c4ce8aba2)

Esperamos a que implemente y cree todo lo que le acabamos de especificar.

![image](https://github.com/user-attachments/assets/8750de95-0d45-4c03-b4b9-afb36ee6c856)

Y como vemos nos saldrá algo así.

![image](https://github.com/user-attachments/assets/a3edd080-7842-48ef-843c-c7deaf818ca4)

## Creación de EC2 y Firewall

Ahora debemos de crear una instancia con su respectivo firewall. Para ello buscamos EC2 y le damos a donde pone lanzar instancia.

![image](https://github.com/user-attachments/assets/0e13c838-eefb-4d3a-aa10-c6d374c0431e)

A continuación, le ponemos un nombre, elegimos el sistema operativo que deseemos, en este caso será ubuntu.

![image](https://github.com/user-attachments/assets/d22e1f2e-7910-408a-ab59-66ce32794a54)

En las claves, usamos vockey, y en configuración de red usaremos la VPC que hemos creado anteriormente. Ahora en grupos de seguridad, creamos uno con el nombre que queramos y le añadimos una regla de entrada más.

![image](https://github.com/user-attachments/assets/00c9023d-512f-4309-bfce-372c226f5d42)

Esa regla de entrada es con http desde cualquier parte, y le dmos a lanzar instancia.

![image](https://github.com/user-attachments/assets/6c1985ae-4186-42eb-81c0-e2b7b0f751fd)

Una vez lanzada deberá aparecer en instancias la que acabamos de crear.

![image](https://github.com/user-attachments/assets/0daab50c-0523-4d21-a9e1-14c2ee7fd110)

Para comprobar que se ha realizado correctamente, nos intentamos conectar a este en mi caso a través de PuTTy.

![image](https://github.com/user-attachments/assets/fde51ff0-aff2-4724-bdbd-3ef78db7e924)

## Instalación de Apache y PHP
Lo primero es actualizar el ubuntu junto a todos sus paquetes y repositorios.

![image](https://github.com/user-attachments/assets/87318902-d3ec-4662-8726-4f563d7606a8)

Ahora instalamos apache
```
sudo apt install apache2
```
![image](https://github.com/user-attachments/assets/63f29bc5-ff38-44d0-add6-2b44b63c3d14)

Ahora lo iniciamos y activamos.
```
sudo systemctl start apache2
sudo systemctl enable apache2
```
![image](https://github.com/user-attachments/assets/2f3fb676-1db4-45ce-aaab-c537c123c779)

Para comprobarlo, en un navegador ponemos la IP pública de la instancia.

![image](https://github.com/user-attachments/assets/0e529fcc-ac2f-4b76-bc09-9844a62921ef)

Ahora vamos con la instalación de PHP. Primero debemos de añadir el repositorio:
```
sudo add-apt-repository ppa:ondrej/php
```
![image](https://github.com/user-attachments/assets/35ac513c-29bc-4fb6-a90d-6d3deed96e38)

Y comenzamos con la instalación:
```
sudo apt install php7.4 libapache2-mod-php7.4 php7.4-cli
```
![image](https://github.com/user-attachments/assets/0ab137c2-cfc6-41dc-a3bc-762954a0bb85)

También debemos de instalar Mysql aparte:
```
sudo apt install php7.4-mysql
```
![image](https://github.com/user-attachments/assets/e2607e14-f85b-4364-ba2b-149c7ee4e040)

Reiniciamos apache:
```
sudo systemctl restart apache2
```
![image](https://github.com/user-attachments/assets/ec1d492d-9ba7-434d-ac97-25083a9cf252)

Y comprobamos:
```
php -v
```
![image](https://github.com/user-attachments/assets/162d5a2d-18a2-4f1b-9b92-9255444af903)

## Creación de la base de datos

Para crear una base de datos en AWS, escribimos RDS en el buscador. quí dentro nos dirigimos a base de datos y le damos a crear una.

![image](https://github.com/user-attachments/assets/4a4d6450-c04b-43f9-8637-6af73267ace7)

Ahora elegiremos la capa estándar de MySQL.

![Captura de pantalla 2025-02-19 124041](https://github.com/user-attachments/assets/e38cc97b-8b10-4848-bc4f-dba02c06967c)

Aquí muy importante seleccionar la capa gratuita.

![image](https://github.com/user-attachments/assets/4fb35012-1e64-4c23-ad28-b2cfb4422ea9)

Le ponemos un nombre a la base de datos y un usuario con su respectiva contraseña.

![image](https://github.com/user-attachments/assets/e5e4d78c-c763-4cff-9b93-6672364d49e7)

En la configuración de la instancia y de el almacenamiento, lo dejamos tal y como viene.

![image](https://github.com/user-attachments/assets/17ebcf51-4d9d-4593-87bc-d8737ba7b26d)

En la parte de conectividad, seguimos la foto de a continuación.

![image](https://github.com/user-attachments/assets/005573b1-29d5-4534-826d-a43364a3b6f7)

Y por último, en configuración adicional, debemos de poner el nombre de la base de datos.

![image](https://github.com/user-attachments/assets/e8deb547-7a1f-42e8-9690-120b93d59e4f)

Esperamos a que se cree.

![image](https://github.com/user-attachments/assets/b583773b-5536-45e9-aa72-a3008b40b6eb)

Y listo

![image](https://github.com/user-attachments/assets/4769f57e-d667-4e21-9dc8-d76e52b24fca)

Ahora debemos de configurarla en un EC2, y para ello seguimos esta imagen.

![image](https://github.com/user-attachments/assets/996f0c93-433a-4860-a4bd-376ee981b5b7)

Elegimos nuestra EC2 creada anteriormente.

![image](https://github.com/user-attachments/assets/b2ac868a-01a6-45a9-b912-544b9a17d649)

Y le damos a configurar.

![image](https://github.com/user-attachments/assets/83f09027-0f9a-4e96-8061-bcd13632bef3)

Y listo

![image](https://github.com/user-attachments/assets/1d9d33c2-5f5c-4a8e-b572-f2234aa61bd9)

Para comprobar si funciona usamos este comando:
```
mysql -h puerto_de_enlace_BD -u admin -p
```

![image](https://github.com/user-attachments/assets/58a2cf02-1659-4aa0-972b-e4dd3fc6a1e8)

## Implementación de EFS

Para crear el sistema de almacenamiento Elastic File System, buscamos EFS en el buscador y le damos a sistemas de archivo, aquí dentro le damos a crear.

![image](https://github.com/user-attachments/assets/42993879-fa48-43ee-be4c-4b0c0db7f219)

Aquí dentro le damos un nombre y elegimos la VPC creada anteriormenete.

![image](https://github.com/user-attachments/assets/b77fb185-ddfb-4a8d-b3f5-38fd3cf84636)

Comprobamos que se ha creado con éxito.

![image](https://github.com/user-attachments/assets/10e2f15c-1dfe-46c3-adfd-8ef66da1c367)

Hay que diriguirse a VPC y añadir una nueva regla de entrada.

![image](https://github.com/user-attachments/assets/11074ee4-efd6-47a5-9452-412d11d3871d)

Aquí ponemos el protocolo NFS que sea conectable a través de la VPC.

![image](https://github.com/user-attachments/assets/6c09e283-fff6-4c26-9674-cbac77e5a275)

En EFS, en la sección de red vamos a cambiar la VPC por la nuestra.

![image](https://github.com/user-attachments/assets/9b59e086-3519-4a87-b22c-b2345bc6e493)

Ahora vamos a asociarla con la maquina de ubuntu.

![image](https://github.com/user-attachments/assets/9170f824-0160-4422-84b1-abe49c6e996f)

Le damos a asociar mediante IP, seleccionamos la subred que hayamos puesto en nuestra VPC, en este caso da igual cual sea. Copiamos el código ese y lo pegamos en la máquina.

![image](https://github.com/user-attachments/assets/5820308b-87a8-4911-813e-4fdf4ef61685)

Primero debemos de instalar NFS con este comando.
```
sudo apt install nfs-common
```

![image](https://github.com/user-attachments/assets/54f6b582-39ba-421d-870e-e2f26e53f81a)

Ahora ejecutamos el comando que nos decía EFS y listo
```
sudo mount -t nfs4 -o nfsvers=4.1,rsize=1048576,wsize=1048576,hard,timeo=600,retrans=2,noresvport 10.2.0.69:/ efs
```

![image](https://github.com/user-attachments/assets/d82374bb-0de0-4e85-97f8-c8a9c6b08d68)

Si salta este error: mount.nfs4: mount point efs does not exist hay que crear el directorio efs:
```
sudo mkdir -p efs
```

## Instalación de Wordpress

Para instalar Wordpress hay que descargarselo desde su página oficial.
```
sudo wget http://wordpress.org/latest.tar.gz
```
Descomprimir el archivo:
```
sudo tar -xf latest.tar.gz
```
Y como vemos ha sido todo un éxito.
![image](https://github.com/user-attachments/assets/bc64469c-1a13-4dd4-a600-4bc33f8edc14)

Ahora necesitamos un cliente de MySQL ya que necesitamos crear una base de datos para wordpress.
```
sudo apt install mysql-client -y
```
![image](https://github.com/user-attachments/assets/c20875c1-f1fb-446e-a1ec-f9f910595864)

Y entramos en MySQL:
```
mysql -h bdwordpress.chn38fhjqphr.us-east-1.rds.amazonaws.com -u admin -p
```
![image](https://github.com/user-attachments/assets/360cc13f-1360-4df5-9170-5eacaf1c8af0)

Creamos la base de datos:
```
CREATE DATABASE wordpress;
CREATE USER 'wordpress_user'@'%' IDENTIFIED BY 'password123';
GRANT ALL PRIVILEGES ON wordpress.* TO 'wordpress_user'@'%';
FLUSH PRIVILEGES;
```
![image](https://github.com/user-attachments/assets/b920cd54-e78b-4e4e-bad0-790fb8d23364)

Y seguimos con el formulario:

![image](https://github.com/user-attachments/assets/4cae4962-22f8-4727-b4a5-56efe99cf815)

Ahora entramos en la DNS pública de nuestra máquina desde el navegador y en nuestra IP ponemos wordpress.

![image](https://github.com/user-attachments/assets/a840e35b-1403-4940-83d1-4443ac631dbb)

Y seguimos con los formularios siguientes.

![image](https://github.com/user-attachments/assets/b1a8becf-02f5-4611-86ba-8a1e6ee60984)

asd

asd

![image](https://github.com/user-attachments/assets/b56ac800-ce61-4522-ba17-c59016c8c7d7)

asd


asd

![image](https://github.com/user-attachments/assets/790ac019-1de0-43f1-b0d7-5fb4433e2916)

asd

![image](https://github.com/user-attachments/assets/a2bcb3c3-afd6-4ab9-9a7d-6e846a8c792e)

asd

![image](https://github.com/user-attachments/assets/e665aa0e-4951-4c3e-86bc-6e9e5991a2f7)

asd

![image](https://github.com/user-attachments/assets/0aff3a2b-4ae9-4e30-90e4-9115ae968f40)
