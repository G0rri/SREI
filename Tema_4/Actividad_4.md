# Volúmenes docker

Los volúmenes Docker permiten almacenar datos fuera de los contenedores en un directorio gestionado por Docker. Se encuentran en /var/lib/docker/volumes en sistemas Linux y son ideales para:

--> Compartir datos entre contenedores.

--> Hacer copias de seguridad.

--> Almacenar datos en la nube.

## Crear un volumen Docker

Para crear un volumen usamos el comando 'volume create':
```
sudo docker volume create mi_volumen
```
![imagen](https://github.com/user-attachments/assets/30312497-a7c2-49ad-9408-51bd240c7702)

## Ver la lista de volúmenes disponibles

```
sudo docker volume ls
```

## Inspeccionar un volumen

```
sudo docker volume inspect mi_volumen
```

## Usar un volumen en un contenedor

```
sudo docker run -d --name contenedor1 -v mi_volumen:/data nginx
```

## Eliminar un volumen

```
sudo docker volume rm mi_volumen
```

# Bind mounts
