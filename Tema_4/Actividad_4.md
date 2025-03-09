## Volúmenes docker

Los volúmenes Docker permiten almacenar datos fuera de los contenedores en un directorio gestionado por Docker. Se encuentran en /var/lib/docker/volumes en sistemas Linux y son ideales para:

--> Compartir datos entre contenedores.

--> Hacer copias de seguridad.

--> Almacenar datos en la nube.

### Crear un volumen Docker

Para crear un volumen usamos el comando 'volume create':
```
sudo docker volume create mi_volumen
```
![imagen](https://github.com/user-attachments/assets/30312497-a7c2-49ad-9408-51bd240c7702)

### Ver la lista de volúmenes disponibles

Para ver si lo hemos creado correctamente, usamos ls para mostrar los volumenees:
```
sudo docker volume ls
```
![imagen](https://github.com/user-attachments/assets/854f6811-446c-422e-af75-d52a35dab127)

### Inspeccionar un volumen

Para inspeccionar un volumen usamos el comando inspect:
```
sudo docker volume inspect mi_volumen
```
![imagen](https://github.com/user-attachments/assets/c042564f-609a-40d9-acb7-57c84fa28604)

### Usar un volumen en un contenedor

Para usar un volumen en específico para un contenedor, se lo especificamos con esto usando la imagen en este caso de hello-world:
```
sudo docker run -d --name contenedor1 -v mi_volumen:/data hello-world
```
![imagen](https://github.com/user-attachments/assets/be541ca5-45ee-4eb3-a830-17b9ed23e86d)

### Eliminar un volumen

Para eliminar un volumen solo le debemos de especificar el 'rm' delante del 'volume'. OJO, si está en uso ese volumen no podrás eliminarlo, por ello elimina el contenedor al que lo tengas vinculado o desvincúlalo.
```
sudo docker volume rm mi_volumen
```
![imagen](https://github.com/user-attachments/assets/8234dcfa-12dc-4488-ada3-10309ef25051)

## Bind mounts

Los bind mounts permiten mapear un directorio o archivo del sistema anfitrión dentro del contenedor. A diferencia de los volúmenes, los bind mounts permiten que el usuario tenga control directo sobre los datos.

### Crear un bind mount

Para crear un bind, primero lo usaremos en un directorio concreto para no liarnos y necesitaremos de un archivo html también. Por último crearemos un docker con la ruta anteriormente especificada con la imagen docker en este caso de nginx.
```
sudo mkdir ~/datos_host
echo "Hola, Docker!" > ~/datos_host/index.html
sudo docker run -d --name contenedor2 -v ~/datos_host:/usr/share/nginx/html nginx
```
![imagen](https://github.com/user-attachments/assets/1c1848fb-b030-4dac-bf0c-fbec8d06ceaf)
![imagen](https://github.com/user-attachments/assets/a311be3b-b72a-4b51-97e5-b5d4ef5db1f0)
![imagen](https://github.com/user-attachments/assets/04a7b389-9f75-46f8-ad52-6372963a7d0d)
![imagen](https://github.com/user-attachments/assets/75bc12d6-953c-4fce-b429-e11da377f183)

### Verificar que el archivo se encuentra dentro del contenedor

Para ver si se encuentra dentro del contenedor, usamos:
```
sudo docker exec -it contenedor2 cat /usr/share/nginx/html/index.html
```
![imagen](https://github.com/user-attachments/assets/275c0ac6-59eb-4838-90c0-04e9faeed76a)

### Eliminar el contenedor sin perder los datos

Para eliminar el contenedor sin perder los datos usamos:
```
sudo docker rm -f contenedor2
```
![imagen](https://github.com/user-attachments/assets/3e9a454e-a2ef-4d2a-a3cd-d91490deed07)

Y como vemos en la imagen los datos se siguen guardando.

## Asociando almacenamiento a los contenedores: volúmenes Docker

Lo primero es crear un volumen, para ello:
Para crear un volumen usamos el comando 'volume create':
```
sudo docker volume create mi_volumen
```
![imagen](https://github.com/user-attachments/assets/6ef61031-6269-4547-bcb7-70918d8644ab)

Ahora crearemos un contenedor con el volumen asociado anteriormente creado.
```
sudo docker run -d --name my-apache-app -v miweb:/usr/local/apache2/htdocs -p 8080:80 httpd:2.4
```
![imagen](https://github.com/user-attachments/assets/320c78c6-9f73-46e7-bb26-70e845eaf985)

Continuamos ejecutando el contenedor y le añadimos algo al html que tenemos que crear, para poder mostrar algo:
```
sudo docker exec my-apache-app bash -c 'echo "<h1>Hola</h1>" > /usr/local/apache2/htdocs/index.html'
```
![imagen](https://github.com/user-attachments/assets/0c757b47-0c78-46f8-8ff9-39cc6f5ec895)

Para ver si ha salido bien, hay 2 formas de comprobarlo, desde el navegador o desde la consola con curl:
```
sudo curl http://localhost:8080
```
![imagen](https://github.com/user-attachments/assets/ddeb1a54-0128-4c88-b593-dfbf24f1c73f)

Ahora borramos el contenedor y creamos otro distinto para ver si la información se pierde:
```
Borramos:
sudo docker rm -f my-apache-app

Creamos:
sudo docker run -d --name my-apache-app -v miweb:/usr/local/apache2/htdocs -p 8080:80 httpd:2.4

Comprobamos:
sudo curl http://localhost:8080
```
![imagen](https://github.com/user-attachments/assets/57e19c68-8b84-40a4-9746-ea7241465cab)
Y listo, se ha vuelto a asociar otro volumen perfectamente.

## Asociando almacenamiento a los contenedores: bind mount

Ahora vamos a algo similar al anterior ejemplo pero con bind mount. Así que lo primero que debemos de hacer es crear un directorio para centralizar el trabajo. Y una vez hecho crearemos un html para mostrar algo:
```
sudo mkdir web
sudo chmod 777 web
cd web
sudo echo "<h1>Hola</h1>" > index.html
ll
```
![imagen](https://github.com/user-attachments/assets/3429458e-9b3e-4fa1-afcf-efd09ab2cdfc)

Continuamos montando en el anterior directorio un contenedor con:
```
sudo docker run -d --name <ejemplo3> -v /home/usuario/web:/usr/local/apache2/htdocs -p 8080:80 httpd:2.4
```
![imagen](https://github.com/user-attachments/assets/4c37c3dc-19ca-4a60-9258-86f327ba5928)

Y lo comprobamos:

![imagen](https://github.com/user-attachments/assets/cf227184-b7dc-4909-90aa-137d00510ecf)

Y ahora borramos, creamos otro y lo volvemos a asociar:
```
Borramos:
sudo docker rm -f my-apache-app

Creamos:
sudo docker run -d --name my-apache-app -v /home/usuario/web:/usr/local/apache2/htdocs -p 8080:80 httpd:2.4

Comprobamos:
sudo curl http://localhost:8080
```
![imagen](https://github.com/user-attachments/assets/b016a234-e258-4a76-8104-86169b5b4dff)

Y listo.

# Ejemplo 1
## Despliegue de la aplicación Guestbook

Primero creamos una red llamada red_guestbook. Luego creamos un contenedor y lo asociamos a esta red. Y por último para poder visualizarla le añadimos un puerto.
```
sudo docker network create red_guestbook
sudo docker run -d --name redis --network red_guestbook -v /opt/redis:/data redis redis-server --appendonly yes
sudo docker run -d -p 80:5000 --name guestbook --network red_guestbook iesgn/guestbook
```
![imagen](https://github.com/user-attachments/assets/70a6ad9c-6813-46c2-a406-ebe888c216a8)

Lo comprobamos:
```
localhost
```
![imagen](https://github.com/user-attachments/assets/bef29c9b-55d4-4a3c-8767-3b2b0970721d)

## Configuración de la aplicación guestbook

Para poder configurarla debemos de ponerle otro nombre y configurarlo especificando puertos y redis_server.
```
sudo docker run -d --name contenedor_redis --network red_guestbook -v /opt/redis:/data redis redis-server --appendonly yes
sudo docker run -d -p 80:5000 --name guestbook -e REDIS_SERVER=contenedor_redis --network red_guestbook iesgn/guestbook
```
![imagen](https://github.com/user-attachments/assets/1a4bd040-31fe-483d-9a81-31b88f9ddf80)

# Ejemplo 2
## Despliegue de la aplicación Temperaturas

Creamos la red de la app que queremos desplegar, y la ejecutamos igual que en el anterior:
```
sudo docker network create red_temperaturas
sudo docker run -d --name temperaturas-backend --network red_temperaturas iesgn/temperaturas_backend
sudo docker run -d -p 80:3000 --name temperaturas-frontend --network red_temperaturas iesgn/temperaturas_frontend
```
![imagen](https://github.com/user-attachments/assets/cae17d38-5f7b-41b5-9a57-b0a9f56641a9)

Comprobamos
```
localhost
```
![imagen](https://github.com/user-attachments/assets/67955d64-4695-4b4d-9d08-502b169ab072)

# Ejemplo 3
## Despliegue de Wordpress + mariadb

Creamos una red para wordpress, pero antes paramos todos los contenedores:
```
sudo docker network create red_wp
```
![imagen](https://github.com/user-attachments/assets/2dc4eb39-6cf8-46f8-97ef-c5387fee1595)

Ejecutamos el docker de mysql para tener una base de datos:
```
sudo docker run -d --name servidor_mysql \
                --network red_wp \
                -v /opt/mysql_wp:/var/lib/mysql \
                -e MYSQL_DATABASE=bd_wp \
                -e MYSQL_USER=user_wp \
                -e MYSQL_PASSWORD=asdasd \
                -e MYSQL_ROOT_PASSWORD=asdasd \
                mariadb
```
![imagen](https://github.com/user-attachments/assets/a8071c3a-22d6-401b-8921-23750d4876af)

Ejecutamos el docker de wordpress:
```
sudo docker run -d --name servidor_wp \
                --network red_wp \
                -v /opt/wordpress:/var/www/html/wp-content \
                -e WORDPRESS_DB_HOST=servidor_mysql \
                -e WORDPRESS_DB_USER=user_wp \
                -e WORDPRESS_DB_PASSWORD=asdasd \
                -e WORDPRESS_DB_NAME=bd_wp \
                -p 80:80 \
                wordpress
```
![imagen](https://github.com/user-attachments/assets/b19cc7aa-f564-4ffa-94be-4edab8828792)

Comprobamos:
```
localhost
```
![imagen](https://github.com/user-attachments/assets/5968f866-9c21-450d-9ec0-b80de75d759b)
