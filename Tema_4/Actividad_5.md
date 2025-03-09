# Ejemplo 1
### Instalación y Verificación de Docker Compose V2

Cuando trabajamos con aplicaciones que requieren múltiples servicios, como una base de datos y un servidor web, es recomendable usar Docker Compose para gestionar los contenedores de manera eficiente. Docker Compose permite definir y ejecutar aplicaciones multicontenedor mediante un archivo YAML.

Primero vamos a ver si tenemos instalado docker compose, para ello:
```
sudo docker compose version
```
![imagen](https://github.com/user-attachments/assets/95f0b21a-191e-4db3-9f56-a4c70f2d525d)

### Levantar los contenedores con Docker Compose

Ahora debemos de despertar los contenedores docker compose. Para ello escribimos esto:
```
sudo docker compose up -d
```
![imagen](https://github.com/user-attachments/assets/5c1bf3d8-5a81-4140-92d0-ef996d56b3c1)

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



