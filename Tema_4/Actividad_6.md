# Ejemplo 1
## Construcción de imágenes con una página estática
### Desde una imagen base

Debemos de descargar un archivo de prueba que contenga un archivo html y un dockerfile. Una vez descargado lo descomprimimos y vemos si está todo lo que necesitaremos. En caso de duda sobre el fichero dockerfile, ver dentro si cumple las espectativas.
```
sudo unzip Descargas/version1.zip
cd version1
ls
nano Dockerfile
```
![imagen](https://github.com/user-attachments/assets/999f5504-708a-42bb-ac94-8b6fbbbf7604)

Construimos el contenedor con el ejemplo descargado:
```
sudo docker build -t josedom24/ejemplo1:v1 .
```
![imagen](https://github.com/user-attachments/assets/93ccdcb2-4483-492e-9061-a9aeb940a429)

Vemos que se haya creado correctamente y lo ejecutamos en el puerto 80:
```
sudo docker images
sudo docker run -d -p 80:80 --name ejemplo1 josedom24/ejemplo1:v1
```
![imagen](https://github.com/user-attachments/assets/ea95eb38-f625-4e6b-be78-36905e54e359)

Y comprobamos:

![imagen](https://github.com/user-attachments/assets/8303a964-e1ae-41f8-9d21-1c795aafdac7)

### Desde una imagen con apache2

La diferencia con respecto al anterior está en editar el fichero Dockerfile del ejemplo1 y poner esto:
```
# syntax=docker/dockerfile:1
FROM httpd:2.4
COPY public_html /usr/local/apache2/htdocs/
EXPOSE 80
```

Construimos el contenedor con el ejemplo modificado:
```
sudo docker build -t josedom24/ejemplo1:v2 .
sudo docker run -d -p 80:80 --name ejemplo1 josedom24/ejemplo1:v2
```

Y comprobamos:

![imagen](https://github.com/user-attachments/assets/5add95e3-38a4-47f1-9a62-be64f03bb2a9)

### Desde una imagen con nginx

Aquí lo mismo, deberemos de editar otra vez el archivo Dockerfile:
```
# syntax=docker/dockerfile:1
FROM nginx:1.24
COPY public_html /usr/share/nginx/html
EXPOSE 80
```

Construimos el contenedor con el ejemplo modificado:
```
sudo docker build -t josedom24/ejemplo1:v3 .
sudo docker run -d -p 80:80 --name ejemplo1 josedom24/ejemplo1:v3
```

Y comprobamos:

![imagen](https://github.com/user-attachments/assets/12b1a126-7e9a-4f40-811d-d86c66708c54)

# Ejemplo
## Construcción de imágenes con una una aplicación PHP
### Desde una imagen base

Aquí debemos de poner esto en el dockerfile y se encargará de todos los requisitos necesarios:
```
# syntax=docker/dockerfile:1
FROM debian:stable-slim
RUN apt-get update && apt-get install -y apache2 libapache2-mod-php7.4 php7.4 && apt-get clean && rm -rf /var/lib/apt/lists/* && rm /var/www/html/index.html
COPY app /var/www/html/
EXPOSE 80
CMD apache2ctl -D FOREGROUND
```
![imagen](https://github.com/user-attachments/assets/66594d7d-172d-4e42-a070-afa68c32db76)

Antes de construirlo debemos de crear el directorio que le hemos especificado al archivo de antes, es decir /app:
```
sudo mkdir app
sudo docker build -t josedom24/ejemplo2:v1 .
```
![imagen](https://github.com/user-attachments/assets/fad6cbd9-500f-49f9-8ac6-fb6c3c8623f0)

asd
```

```
![imagen](https://github.com/user-attachments/assets/2ae632ff-b9f1-489c-a027-fb9b609a63ee)

asd
```

```

asd
```

```

asd
```

```

asd
```

```

asd
```

```

asd
```

```

asd
```

```
