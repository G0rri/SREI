# Scripts 

## Script de puerto Listen
Para realizar los siguientes scripts, en cada carpeta que vamos a editar, vamos a tener que proporcionar ciertos permisos para poder permitir la edición de estos.

![image](https://github.com/user-attachments/assets/00a738a6-2db8-4ee8-b7b1-ce909f9a016b)

Para empezar debemos de crear el script mediante un editor de texto, en esta ocasión utilizaremos gedit. 

En esta parte del código le preguntamos si se ha introducido un valor válido.

````
if [$# -eq 0];
  then echo "Error"
````

Aquí analizamos todas las lineas del archivo ports.conf, en busca de la palabra Listen con el parámetro introducido($1).

````
elif
  grep -q "Listen $1" "etc/apache2/ports.conf";
  then echo "El puerto ya existe en ports.conf"
````

En esta parte de código, mostramos lo que queremos escribir junto al parámetro que le adjuntaremos al ejecutarlo. Esto lo copiará en la ruta marcada, mostrandonos un mensaje de confirmación.

````
else 
	echo "Listen $1" >> "/etc/apache2/ports.conf"
	echo "El puerto ha sido añadido al archivo de configuración"
sleep 3
clear
fi
````

![image](https://github.com/user-attachments/assets/89aab286-9cc2-4970-bac8-6803036fe07c)

Para comprobar si funciona correctamente, escribimos sudo bash (el nombre del fichero) y el número del puerto. Como vemos en la imagen, yo ya había creado ese puerto anteriormente y por ende me muestra que ya está creado.

![image](https://github.com/user-attachments/assets/97386953-fe3d-40ec-84f1-5aa45939db57)


Comprobar si se ha proporcionado la IP y el dominio como argumento.
Comprobar si el dominio existe en el fichero host.
Añadir el dominio y la ip al fichero host.

![image](https://github.com/user-attachments/assets/682ce052-c910-4cc7-a6d8-7e90cdcbb1c7)



asd

asd

asd
