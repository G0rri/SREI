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
(La imagen la he perdido, se me olvidó guardarla)

Descargamos los clientes respectivamente.
```
sudo apt-get install mariadb-server mariadb-client -y
```
(La imagen la he perdido, se me olvidó guardarla)

Ahora activamos todos los servicios que hagan falta para la atenticación.
```
sudo a2enmod authn_dbd
sudo a2enmod authn_socache
sudo a2enmod socache_shmcb
sudo a2enmod dbd
```
![image](https://github.com/user-attachments/assets/3e3b09ec-9041-4604-b7e0-650b21c1bf8f)

Ahora creamos una base de datos.
```
mysqladmin -u root -p create awsdb
```
![image](https://github.com/user-attachments/assets/7eaa8988-805e-4e09-a85f-1ef07842caba)

Una vez creamos la base de datos, vamos a configurar unos cuantos parámetros. Por ello entramos dentro de mysql.
```
sudo mysql -u root -p
```
![image](https://github.com/user-attachments/assets/e991299d-28c2-4747-8a24-62778cbbcffc)

Luego añadimos privilegios.
```
GRANT SELECT, INSERT, UPDATE, DELETE ON awsdb.* TO 'aws_admin'@'localhost' IDENTIFIED BY 'aws_admin_password';
GRANT SELECT, INSERT, UPDATE, DELETE ON awsdb.* TO 'aws_admin'@'localhost.localdomain' IDENTIFIED BY 'aws_admin_password';
```
![image](https://github.com/user-attachments/assets/30e4bf70-486b-46d8-b38f-3ef5cca67ad5)
![image](https://github.com/user-attachments/assets/e9f7e29a-7875-4643-941a-136596467cc0)

Limpiamos los privilegios con:
```
flush privileges
```
![image](https://github.com/user-attachments/assets/3e8c1c27-0a02-419d-aaec-9f3c9ed3e10a)

Una vez hecho lo anterior vamos a meternos en la base de datos. Para que haya una autenticación debe de haber un usuario con privilegios y que esté permitido. Por ello vamos a crear una tabla para aquellos que puedan autenticarse.
```
use aws_db;
create table mysql_auth ( username varchar(191) not null, passwd varchar(191), groups varchar(191), primary key (username) );
```
![image](https://github.com/user-attachments/assets/499142a9-6bd9-40bd-80d4-5f5a852a4ed9)

Ahora pasaremos la contraseña a formato hash, en concreto a SHA1.

```
htpasswd -bns user  user
```
![image](https://github.com/user-attachments/assets/18cdb0ec-c894-4f14-bdc8-0fd2890fdee5)

Este hash junto al nombre del usuario y del grupo, hay que instertarlo dentro de la tabla mysql_auth.
```
INSERT INTO `mysql_auth` (`username`, `passwd`, `groups`) VALUES('user', '{SHA}Et6pb+wgWTVmq3VpLJlJWWgzrck=', 'usergroup');
```
![image](https://github.com/user-attachments/assets/17f20052-3121-4d34-80f2-6219f75e758f)

Ahora teniendo la base de dato con autenticación necesitaremos una página web vinculada a esta db para poder mostralo. Para esto creamos un directorio que permita mostrarlo.
```
sudo mkdir /var/www/html/aws
```
![image](https://github.com/user-attachments/assets/aa3aa633-0aff-431d-8e88-e31085600bbd)

Ponemos esto en el .conf.
```
 DBDriver mysql
        DBDParams "dbname=awsdb user=aws_admin pass=aws_admin_password"

        DBDMin 4
        DBDKeep 8
        DBDMax 20
        DBDExptime 300

<Directory "/var/www/html/aws">
        AuthType Basic
        AuthName "My Server"

        AuthBasicProvider socache dbd

        AuthnCacheProvideFor dbd
        AuthnCacheContext my-server

        Require valid-user

        AuthDBDUserPWQuery "SELECT passwd FROM mysql_auth WHERE username = %s"
</Directory>

```
![image](https://github.com/user-attachments/assets/7eb8f0ea-f40b-4a0d-a15e-da49e8d30217)

Reiniciamos apache
```
sudo service apache2 reload
```
