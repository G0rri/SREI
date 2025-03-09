## Descarga la imagen de ubuntu
![imagen](https://github.com/user-attachments/assets/7b3e9f82-8922-46ca-b0f8-87acad644f64)

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

Para mostrar todos los contenedores en ejecución usamos ps.
```
sudo docker ps
```
![imagen](https://github.com/user-attachments/assets/2fb33a25-85bb-4aa6-8fbd-7eb54242fcf5)

## Para el contenedor "myhello1”

Para parar un contenedor usamos stop y el nombre.
```
sudo docker stop myhello1
```
![imagen](https://github.com/user-attachments/assets/ecdc4dd5-11da-40e6-a8d1-7a8b5d140114)

## Para el contenedor "myhello2”

Lo mismo que en el anterior.
```
sudo docker stop myhello2
```
![imagen](https://github.com/user-attachments/assets/cadb350a-231d-41a5-aa49-190fc5042e1c)

## Borra el contenedor “myhello1”

Para borrarlo es como en los archivos, usamos rm.
```
docker rm myhello1
```
![imagen](https://github.com/user-attachments/assets/34e94932-1a0a-4d2f-a0b7-79552b190ef9)

Para ver si ha surtido efecto, volvemos a ver todos los contenedores. Y como vemos en la imagen falta el que acabamos de eliminar:
![imagen](https://github.com/user-attachments/assets/290da5a5-5190-40ac-abe7-630bf6367e50)

## Muestra los contenedores que se están ejecutando.

Para mostrar todos los contenedores en ejecución usamos ps.
```
sudo docker ps
```
![imagen](https://github.com/user-attachments/assets/3a2298dd-554c-43ef-a6e0-d64608413428)

## Borra todos los contenedores

Para eliminar todos los contenedores, primero deberemos de parar todos, y para eso usamos:
```
docker stop $(docker ps -q)
```
![imagen](https://github.com/user-attachments/assets/3b8218fe-8ca6-4dea-b112-d6388ae00ca7)

Y ahora procedemos a eliminar todos los contenedores con:
```
sudo docker rm $(docker ps -a -q)
```
![imagen](https://github.com/user-attachments/assets/69f60a4c-b1ad-4d41-9ee9-d15eb6c5109e)

Como vemos en la comprobación, todos y cada uno han sido eliminados.
