# Actividad 0.4 - Usando cURL

Busca información sobre el comando curl y muestra al menos cinco ejemplos de uso

## ¿Que es cURL?

Es un comando que te permite tanto enviar como descargar datos (entre otras cosas) al/del servidor.

## Ejemplos

+ Para conseguir el documento html de una página web, escribimos:
```
curl https://www.google.com/
```
 ![image](https://github.com/user-attachments/assets/3f271909-0bb7-4d14-af20-d562fb565851)

+ Para descargar un archivo y luego guardarlo con el nombre que tu le pongas, escribimos:

````
curl -o archivo.txt http://google.com/archivo.txt
````

![image](https://github.com/user-attachments/assets/df8902d5-51df-4138-9f68-aef9a52f5aa8)


+  Para guardar el index de una página en un archivo, escribimos:

````
curl http://google.com -o prueba.html
````
![image](https://github.com/user-attachments/assets/42dd12fc-c547-4928-95c4-96ff4008b944)

