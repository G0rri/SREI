# Ejemplo 1
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

# Ejemplo 2
## Asociando almacenamiento a los contenedores: volúmenes Docker

### Usando volúmenes docker
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
