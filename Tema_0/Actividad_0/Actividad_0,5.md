# Actividad 0.5 - Práctica servidor web

## Instalar Python

Es tan fácil como instalar [python](https://www.python.org/downloads/) desde su página web o también puedes hacerlo desde la Microsoft Store.

Una vez iniciado el .exe, veremos estas 2 carpetas.

![image](https://github.com/user-attachments/assets/d20a6014-72f5-4329-a33c-0165f6ac0968)


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
