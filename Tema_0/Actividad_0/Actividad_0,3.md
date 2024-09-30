# Actividad 0.3 - Práctica telnet/http

## ¿Que es telnet?

Es un protocolo de red que permite conectarte a un servidor a través de línea de comandos, aunque cabe añadir que no cifra la información.

## Instalación

Para activar telnet en windows 10 seguimos la imagen de abajo.

![Captura de pantalla 1](https://github.com/user-attachments/assets/fe1c0e4b-8a44-4d73-b268-b9ae8cd018ab)

A continuación probaremos el comando telnet con el ejemplo:
“telnet www.google.com 80” donde telnet es el comando, www.google.com es la url y 80 es el puerto.

![Captura de pantalla 2](https://github.com/user-attachments/assets/3101f2e7-9aeb-42a1-bf64-e12621f87241)

Aparecerá una pestalla en negro, aunque no se vea escribimos ‘GET’ y pulsamos enter.
Nos aparecerá la imagen de abajo:

![Captura de pantalla 3](https://github.com/user-attachments/assets/51aea4b4-ecaa-4234-a597-4dbc7a8ebc2c)

Ahora vamos a hacer lo mismo pero desde una página web en local. Para ello nos descargamos XAMPP, una vez descargado activamos los servicios de apache y MySQL.

![Captura de pantalla 4](https://github.com/user-attachments/assets/4ea2ae5f-7b3e-4363-b1c2-043b0499680a)

Dentro de los archivos del XAMPP, nos vamos a htdocs, y aquí dentro creamos una carpeta (en mi caso práctica). Dentro de ella creamos un archivo html para que veamos algo.

![Captura de pantalla 5](https://github.com/user-attachments/assets/e84a5696-2f22-48bc-a9e1-44ada2d9cbbf)

Ahora escribimos 'localhost/(nombre del archivo de la página web)' en la url del navegador y enter.

![Captura de pantalla 6](https://github.com/user-attachments/assets/c2678419-2673-47a3-a69a-c2968326a909)

Para comprobar que funciona escribimos 'telnet localhost 80'

![Captura de pantalla 7](https://github.com/user-attachments/assets/f384879b-72a6-476b-9ca8-50d6c65af8b5)

Y como vemos hace una petición porque existe esta página.

![Captura de pantalla 8](https://github.com/user-attachments/assets/772c7086-0fd2-43e8-9444-5cc44c78ee35)
