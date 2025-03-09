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
