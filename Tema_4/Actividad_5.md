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
