# Ejemplo 1
## Instalación y Verificación de Docker Compose V2

Cuando trabajamos con aplicaciones que requieren múltiples servicios, como una base de datos y un servidor web, es recomendable usar Docker Compose para gestionar los contenedores de manera eficiente. Docker Compose permite definir y ejecutar aplicaciones multicontenedor mediante un archivo YAML.

Primero vamos a ver si tenemos instalado docker compose, para ello:
```
sudo docker compose version
```
![imagen](https://github.com/user-attachments/assets/95f0b21a-191e-4db3-9f56-a4c70f2d525d)

## Aplicación Web con Nginx y MySQL
### Crear el archivo docker-compose.yaml

Lo primero es crear el archivo docker-compose.yaml con esto dentro:
```
version: '3.8'

services:
  web:
    image: nginx:latest
    ports:
      - "8080:80"
    volumes:
      - ./html:/usr/share/nginx/html
    depends_on:
      - db

  db:
    image: mysql:5.7
    environment:
      MYSQL_ROOT_PASSWORD: example
      MYSQL_DATABASE: mydatabase
      MYSQL_USER: user
      MYSQL_PASSWORD: password
    volumes:
      - db_data:/var/lib/mysql

volumes:
  db_data:
```
![imagen](https://github.com/user-attachments/assets/e9a962eb-1be1-4ba7-920a-7378897448e4)

### Crear el directorio para los archivos HTML

Ahora crearemos un directorio para los archivos html y añadiremos 1:
```
sudo mkdir html
sudo echo "<h1>¡Hola, Docker Compose!</h1>" > html/index.html
```
