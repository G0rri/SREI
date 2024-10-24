# Scripts 

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

![image](https://github.com/user-attachments/assets/89aab286-9cc2-4970-bac8-6803036fe07c)

Comprobar si se ha proporcionado la IP y el dominio como argumento.
Comprobar si el dominio existe en el fichero host.
Añadir el dominio y la ip al fichero host.

![image](https://github.com/user-attachments/assets/ca56e913-399b-4e1a-aab3-3d31af9c4745)


asd

asd

asd
