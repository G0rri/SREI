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
