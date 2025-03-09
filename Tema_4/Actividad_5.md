# Ejemplo 1
### Instalación y Verificación de Docker Compose V2

Cuando trabajamos con aplicaciones que requieren múltiples servicios, como una base de datos y un servidor web, es recomendable usar Docker Compose para gestionar los contenedores de manera eficiente. Docker Compose permite definir y ejecutar aplicaciones multicontenedor mediante un archivo YAML.

Primero vamos a ver si tenemos instalado docker compose, para ello:
```
sudo docker compose version
```
![imagen](https://github.com/user-attachments/assets/95f0b21a-191e-4db3-9f56-a4c70f2d525d)

## Despliegue de la aplicación guestbook

Lo primero es crear el archivo docker-compose.yaml con esto dentro:
```
version: '3.1'
services:
  app:
    container_name: guestbook
    image: iesgn/guestbook
    restart: always
    environment:
      REDIS_SERVER: redis
    ports:
      - 8080:5000
  db:
    container_name: redis
    image: redis
    restart: always
    command: redis-server --appendonly yes
    volumes:
      - redis:/data
volumes:
  redis:
```
![imagen](https://github.com/user-attachments/assets/6ff554c0-fbf9-43d0-92b7-98660960346c)

### Levantar los contenedores con Docker Compose

Ahora debemos de despertar los contenedores docker compose. Para ello escribimos esto:
```
sudo docker compose up -d
```
![imagen](https://github.com/user-attachments/assets/78ea7913-b857-40e2-ad21-caf0590570c6)

Comprobamos:

![imagen](https://github.com/user-attachments/assets/55a0424c-b8ad-4cfb-8352-9802dcab3760)

Para parar los contenedores usamos:
```
sudo docker compose stop
```
Y para eliminarlos:
```
sudo docker compose down -v
```
![imagen](https://github.com/user-attachments/assets/104aa39e-9904-4c37-8c84-302dbdd7a9b0)

# Ejemplo 2
## Despliegue de la aplicación Temperaturas

Modificamos el archivo docker-compose.yaml:
```
version: '3.1'
services:
  frontend:
    container_name: temperaturas-frontend
    image: iesgn/temperaturas_frontend
    restart: always
    ports:
      - "8081:3000"
    environment:
      TEMP_SERVER: temperaturas-backend:5000
    depends_on:
      - backend
  backend:
    container_name: temperaturas-backend
    image: iesgn/temperaturas_backend
    restart: always
```
![imagen](https://github.com/user-attachments/assets/67b8b371-2fed-44bf-ac4a-bd752a8bbfc4)

Ahora lo iniciamos y vemos que se ha creado:
```
sudo docker compose up -d
```
![imagen](https://github.com/user-attachments/assets/8dd2fcc6-1154-4fbe-90df-b2c68517adb1)

Comprobamos:
![imagen](https://github.com/user-attachments/assets/c3c52b12-14f3-446d-b533-44914b8a7c75)

Para parar los contenedores usamos:
```
sudo docker compose stop
```
Y para eliminarlos:
```
sudo docker compose down -v
```
![imagen](https://github.com/user-attachments/assets/104aa39e-9904-4c37-8c84-302dbdd7a9b0)

# Ejemplo 3
## Despliegue de Wordpress + MariaDB
### Utilizando docker

Ahora lo mismo que antes pero con Wordpress y MariaDB, así que modificamos el archivo docker-compose.yaml:
```
version: '3.1'
services:
  wordpress:
    container_name: servidor_wp
    image: wordpress
    restart: always
    environment:
      WORDPRESS_DB_HOST: db
      WORDPRESS_DB_USER: user_wp
      WORDPRESS_DB_PASSWORD: asdasd
      WORDPRESS_DB_NAME: bd_wp
    ports:
      - 80:80
    volumes:
      - wordpress_data:/var/www/html/wp-content
  db:
    container_name: servidor_mysql
    image: mariadb
    restart: always
    environment:
      MYSQL_DATABASE: bd_wp
      MYSQL_USER: user_wp
      MYSQL_PASSWORD: asdasd
      MYSQL_ROOT_PASSWORD: asdasd
    volumes:
      - mariadb_data:/var/lib/mysql
volumes:
    wordpress_data:
    mariadb_data:
```
![imagen](https://github.com/user-attachments/assets/5f4f659e-5359-4043-a759-4b199f5ddbcd)

Lo iniciamos y vemos que se ha creado:
```
sudo docker compose up -d
```
![imagen](https://github.com/user-attachments/assets/1a002d06-68c4-41b9-83ee-a1a6c1520fa3)

Y comprobamos:
![imagen](https://github.com/user-attachments/assets/8c6cf95e-0c0b-4aa4-afd7-89ec5919d443)

Para parar los contenedores usamos:
```
sudo docker compose stop
```
Y para eliminarlos:
```
sudo docker compose down -v
```
![imagen](https://github.com/user-attachments/assets/235200b7-b0bc-43ab-97d1-c6ce8d0ab3f4)

### Utilizando bind-mount

Es igual, pero debemos de cambiar el archivo de docker-compose.yaml:
```
version: '3.1'
services:
  wordpress:
    container_name: servidor_wp
    image: wordpress
    restart: always
    environment:
      WORDPRESS_DB_HOST: db
      WORDPRESS_DB_USER: user_wp
      WORDPRESS_DB_PASSWORD: asdasd
      WORDPRESS_DB_NAME: bd_wp
    ports:
      - 80:80
    volumes:
      - ./wordpress:/var/www/html/wp-content
  db:
    container_name: servidor_mysql
    image: mariadb
    restart: always
    environment:
      MYSQL_DATABASE: bd_wp
      MYSQL_USER: user_wp
      MYSQL_PASSWORD: asdasd
      MYSQL_ROOT_PASSWORD: asdasd
    volumes:
      - ./mysql:/var/lib/mysql
```
![imagen](https://github.com/user-attachments/assets/f406face-feac-4db1-8ca6-4b944486fa8f)

Y repetimos el proceso:

![imagen](https://github.com/user-attachments/assets/81f82cb9-cb10-4352-8455-6dea70ed2152)

Comprobamos:
![imagen](https://github.com/user-attachments/assets/75d647cb-2581-421a-ac5d-a2bed9d51be8)

Para parar los contenedores usamos:
```
sudo docker compose stop
```
Y para eliminarlos:
```
sudo docker compose down -v
```
![Uploading imagen.png…]()
