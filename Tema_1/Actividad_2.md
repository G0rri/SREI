# Conexión con AWS
Para conectarnos a la instancia de AWS mediante SSH, lo haremos coon PuTTY. Para ello necesitaremos de 2 datos:

--> El Host name (or IP address).

![image](https://github.com/user-attachments/assets/034caed2-c779-4216-8b01-38dc87c825ed)


--> Y la clave privada para autenticación.

![image](https://github.com/user-attachments/assets/ec2b67da-30ed-474c-ba85-50acbed85175)

Una vez hecho lo anterior nos descargamos PuTTY y añadimos los datos anteriores.

![image](https://github.com/user-attachments/assets/c39a50e5-0a43-49ec-a2f9-5a92c56809d4)

![image](https://github.com/user-attachments/assets/3e3e265a-1e76-4d68-bf0b-98d90b09a355)

Nos saldrá una alerta de si confiamos.

![image](https://github.com/user-attachments/assets/b975bfd4-f581-4118-aaad-a6097e0e6cc2)

Una vez loggeados ya podremos empezar con la práctica.

![image](https://github.com/user-attachments/assets/883654bc-8ac6-4c97-920a-41f62954ae2e)

## Instalamos Apache
Para realizar la autenticación primero debemos de tener instalado Apache así que por ello realizamos una actualización de todo.
```
sudo apt update
sudo apt upgrade
```
![image](https://github.com/user-attachments/assets/91f994dd-9f4f-4650-96fe-b701d0831c2f)

Ahora comenzamos con la instalación de apache.
```
sudo apt-get install apache2
```
![image](https://github.com/user-attachments/assets/1cc62131-026a-444a-b5a3-4f03915f9862)

# Activar la autenticación con MySql
Continuamos con la instalación de MySQL y PHP para poder crear una autenticación.
```
sudo apt-get install apache2 php7.0 libapruti11-dbd-mysql -y
```
(La imagen la he perdido)
Descargamos los clientes respectivamente.
```
sudo apt-get install mariadb-server mariadb-client -y
```
(La imagen la he perdido)
Y activamos los servicios respectivamente.
```
sudo systemctl enable apache2
sudo systemctl enable mysql
```
(La imagen la he perdido)
Ahora entramos en mysql y creamos una base de datos.
```
sudo mysql -u root -p
create database aws_db;
```
![image](https://github.com/user-attachments/assets/df1d04ba-25a0-4bba-adf0-5bec41e3802c)

Luego añadimos privilegios.
```
GRANT SELECT, INSERT, UPDATE, DELETE ON aws_db.* TO 'defaultsite_admin'@'localhost' IDENTIFIED BY 'usuario';
GRANT SELECT, INSERT, UPDATE, DELETE ON aws_db.* TO 'defaultsite_admin'@'localhost.localdomain' IDENTIFIED BY 'password';
```
![image](https://github.com/user-attachments/assets/7730f222-2e29-4847-aa28-39b6ad85e261)

Limpiamos los privilegios con:
```
flush privileges
```
![image](https://github.com/user-attachments/assets/3e8c1c27-0a02-419d-aaec-9f3c9ed3e10a)

Una vez hecho lo anterior vamos a meternos en la base de datos,
```
use aws_db;
```
![image](https://github.com/user-attachments/assets/4eaa257a-15ff-4486-bca3-d747fe8afaee)

Para que haya una autenticación debe de haber un usuario con privilegios y que esté permitido. Por ello vamos a crear una tabla para aquellos que puedan autenticarse.
```
create table mysql_auth ( username varchar(191) not null, passwd varchar(191), groups varchar(191), primary key (username) );
```
![image](https://github.com/user-attachments/assets/1fd26fe9-be8a-4b4f-91c3-e173c65dbbf6)

Ahora activamos todos los servicios que hagan falta para la atenticación.
```
sudo a2enmod authn_dbd
sudo a2enmod authn_socache
sudo a2enmod socache_shmcb
sudo a2enmod dbd
```
![image](https://github.com/user-attachments/assets/3e3b09ec-9041-4604-b7e0-650b21c1bf8f)

Ahora teniendo la base de dato con autenticación necesitaremos una página web vinculadaa esta db para poder mostralo. Para esto creamos un directorio que permita mostrarlo
