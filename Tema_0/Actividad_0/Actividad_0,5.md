# Actividad 0.5 - Práctica servidor web

## Instalar Python

Es tan fácil como instalar [python](https://www.python.org/downloads/) desde su página web o también puedes hacerlo desde la Microsoft Store.

Una vez iniciado el .exe, veremos estas 2 carpetas.

![image](https://github.com/user-attachments/assets/d20a6014-72f5-4329-a33c-0165f6ac0968)

Debemos ejecutar el .exe de dentro de la carpeta de Python312, que se llama python a secas.

## Ejemplo 1

En mi caso como tengo python instalado en el pen drive, no encontraba la ruta para ejecutar python, por lo que tuve que añadirle este comando para cambiar la ruta: 
````
set PATH=G:\Programs\Python\Python312;G:\Programs\Python\Python312\Scripts;%PATH%
````
Para crear un servidor de web simple, es tan fácil como escribir: 
````phyton
python -m http.server 8000
````

![image](https://github.com/user-attachments/assets/bf294fa4-6a47-4984-a4e8-5450d72a02fa)


Ahora ya habremos creado una página web en local, y si escribimos localhost:8000 en la url del navegador, nos mostrará nuestra página local que son los archivos. Pero antes de eso, vamos a poner que nos muestre una página html por defecto. Para ello creamos una y le ponemos el nombre de index.

![image](https://github.com/user-attachments/assets/54a8c138-f3da-4d40-b1f6-d3e1ee39ff7c)


Como vemos ha funcionado perfectamente y la página principal que nos muestra ahora es el archivo index.

![image](https://github.com/user-attachments/assets/5298170f-98aa-4bda-b7a6-f24017c02113)

## Ejemplo 2

Este ejemplo lo que tenemos que hacer es descargar este [script de python](https://gist.github.com/kabinpokhrel/6fd1275603e9d5f1e284be717cbd1bff#file-server-py), que lo que hace es en gran medida lo mismo que hemos hecho anteriormente, pero solo ejecutando este programa.

En la ruta de abajo se muestra la ruta más cómoda:

![image](https://github.com/user-attachments/assets/6c7ce604-a4f2-4a41-bbf2-604abca7148e)


Ahora abrimos cmd y nos situamos en la ruta donde tengamos descargada el archivo.
Esto se hace con el comando cd para moverte.

````
cd
````

![image](https://github.com/user-attachments/assets/70a0cc54-8633-469a-ae3a-3e1774ffaa4b)


Ahora escribimos el nombre del archivo. Si nos pide con que abrirlo, buscamos el archivo ejecutable de la aplicación de python.

![image](https://github.com/user-attachments/assets/fee9cd0d-f0a5-4354-986a-3ab15e1ee5b7)


Le damos y aparecerá que ya hemos creado una página web a nivel local con python.

![image](https://github.com/user-attachments/assets/08a0893d-ba2b-46f0-9c4e-bcd3206adbc9)


Para comprobarlo, nos vamos a un navegador y escribimos localhost:8000, aquí dentro aparecerán todos los repositorios que hay en ese directorio. Para poner una página de inicio como hicimos en el ejemplo anterior, deberemos de modificar el script.

![image](https://github.com/user-attachments/assets/d2762e22-f6b0-4532-9ed0-74486adb930d)
