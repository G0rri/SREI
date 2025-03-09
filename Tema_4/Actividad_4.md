# Volúmenes docker

## Crear un volumen Docker

```
docker volume create mi_volumen
```

## Ver la lista de volúmenes disponibles

```
docker volume ls
```

## Inspeccionar un volumen

```
docker volume inspect mi_volumen
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
