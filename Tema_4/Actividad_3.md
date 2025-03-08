## Descarga la imagen de ubuntu

Para descargar una imagen utilizamos el comando pull y el nombre de la imagen a descargar.
```
sudo docker pull ubuntu
```
![imagen](https://github.com/user-attachments/assets/4bb8bc09-23cf-4877-9353-bb63608939be)

## Descarga la imagen de hello-world

En este caso como esta imagen ya la teníamos descargada, pues intentará actualizarla:
```
sudo docker pull hello-world
```
![imagen](https://github.com/user-attachments/assets/6584fae9-75eb-4ac7-b972-4822473b0e00)

## Descarga la imagen nginx

Igual que en el primero, realizamos este ajuste en el comando y listo:
```
sudo docker pull nginx
```
![imagen](https://github.com/user-attachments/assets/b3d39a5c-5825-47b3-8e8d-ab9133d50af1)

## Muestra un listado de todas la imágenes

Para ver todas las imagenes, es tan facil como ejecutar este comando:
```
sudo docker images
```
![imagen](https://github.com/user-attachments/assets/ebcafd47-9bde-4565-9ffd-6439fd699aff)

## Ejecuta un contenedor hello-world y dale nombre “myhello1”

Para ejecutar el contenedor hello-world con un seudónimo, usamos este comando:
```
sudo docker run --name myhello1 hello-world
```
![imagen](https://github.com/user-attachments/assets/484f2c39-da30-4b39-bc2d-6cdd9863e79c)

Y comprobamos que se haya hecho correctamente:
```
sudo docker ps -a
```
![imagen](https://github.com/user-attachments/assets/30ea18ad-9551-449f-82a0-f686125e2038)

## Ejecuta un contenedor hello-world y dale nombre “myhello2”

Ahora lo mismo pero cambiando el nombre:
```
sudo docker run --name myhello2 hello-world
```
![imagen](https://github.com/user-attachments/assets/b706dcda-7a59-4268-add7-945fef4708a0)

## Ejecuta un contenedor hello-world y dale nombre “myhello3”

Aquí igual que en el anterior:
```
sudo docker run --name myhello3 hello-world
```
![imagen](https://github.com/user-attachments/assets/14f4d0d8-5574-4b9a-9cd4-52102083eeda)

## Muestra los contenedores que se están ejecutando
## Para el contenedor "myhello1”
## Para el contenedor "myhello2”
## Borra el contenedor “myhello1”
## Muestra los contenedores que se están ejecutando.
## Borra todos los contenedores
