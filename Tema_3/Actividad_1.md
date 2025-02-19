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

## Implementación de EFS

## Instalación de Wordpress
