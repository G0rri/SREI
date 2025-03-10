# Tarea 2
## Ejecuta la imagen "hello-world"

Para ejecutar un contenedor, usamos el comando junto al nombre que queramos ponerle:
```
sudo docker run hello-world
```
![image](https://github.com/user-attachments/assets/fc23319e-fed9-459e-9ec3-e7793eea117d)

## Muestra los contenedores Docker

Para mostrar todos los contenedores usamos:
```
sudo docker ps -a
```
![image](https://github.com/user-attachments/assets/176007a2-c2fa-485e-85bd-bd3dd8b68032)

## Muestra las imágenes Docker instaladas

Y para ver las imagenes de los contenedores:
```
sudo docker images
```
![image](https://github.com/user-attachments/assets/3823c721-91f0-4358-b95d-99f79c3c26ab)

## Edita el fichero Dockerfile

Ahora para añadir una app, primero debemos de añadir donde está alojada esa app, es decir añadimos su repositorio.
```
git clone https://github.com/docker/getting-started-app.git
```
![image](https://github.com/user-attachments/assets/b15c84d6-2ce2-4fb9-be96-41eb7a1e6549)

Ahora creamos un archivo llamado dockerfile y le añadimos esto:
```
FROM node:lts-alpine
WORKDIR /app
COPY . .
RUN yarn install --production
CMD ["node", "src/index.js"]
EXPOSE 3000
```
![image](https://github.com/user-attachments/assets/a04e7874-0d96-4058-94d2-44fb8c883578)

## Construye el contenedor

Ahora construimos esa app:
```
sudo docker build -t getting-started .
```
![image](https://github.com/user-attachments/assets/14b06930-da75-4f01-9137-f9f79baa19f4)

## Ejecútalo

Ahora ejecutamos la app en el puerto :3000:
```
sudo docker run -d -p 127.0.0.1:3000:3000 getting-started
```
![image](https://github.com/user-attachments/assets/e18bfb27-b9ed-4373-b182-731dab65922b)

Ahora en cualquier ordenador si escribimos esta dirección, podremos ver nuestra primera aplicación creada con docker.

![image](https://github.com/user-attachments/assets/e6034e7d-6ed2-4227-a5a9-da8b6f57b962)

## Create una cuenta en hub.docker.com

Ahora debemos de crear una cuenta en hub.docker.com, no voy a hacer fotos de eso porque es registrarse con un correo y una contraseña, no tiene más misterio. 

## Publícalo

Una vez creado, debemos de logearnos dentro de nuestra máquina ubuntu en este caso.
```
sudo docker login -u <usuario>
```
![image](https://github.com/user-attachments/assets/e7e9d75b-ac1e-4833-a89e-9ac22f5885a7)

Ahora para subir la imagen, debemos primero asociarla a nuestra cuenta:
```
sudo docker tag mi-imagen tu-usuario/mi-imagen:latest
```
![imagen](https://github.com/user-attachments/assets/48e1e6e2-cba2-4235-a6cb-5e1c2127b376)

Ahora publicamos la imagen en nuestra cuenta tal que así:
```
sudo docker push tu-usuario/mi-imagen:latest
```
![imagen](https://github.com/user-attachments/assets/4316ca83-3325-4892-8f5e-2b1aa48738eb)

Ahora si nos vamos a la página de docker iniciamos sesión y nos vamos a nuestro perfil, en la sección de repositorios, veremos que hay una imagen subida  que coincide con el id de la imagen que acabamos de publicar a través de ubuntu.

![imagen](https://github.com/user-attachments/assets/649c732d-85d2-434c-a34d-d601366b2a4d)
