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

## Script que añade nombre de dominio e IP
Al principio del script, debemos comprobar si se ha proporcionado la IP y el dominio como argumento. Si no se ha hecho correctamente, se mostrará como se debeusar el script.

````
if [ "$#" -ne 2 ]; then
    echo "Uso: $0 <IP> <dominio>"
    exit 1
fi
````
Creamos 2 variables, y le damos el valor del parámetro 1 y 2. El 1 será la IP y el 2 será el nombre del dominio.

````
IP=$1
DOMINIO=$2
````
Ahora vamos a comprobar si el dominio existe en el fichero host.

````
if grep -q "$DOMINIO" "/etc/hosts"; then
    echo "El dominio '$DOMINIO' ya existe en /etc/hosts."
    exit 1
fi
````
+ Ahora vamos a añadir el nuevo dominio y la IP al fichero host. El comando 'tee -a' lo que hace es añadir el contenido al final del archivo sin reemplazarlo. +
+ El segundo echo mostrará un mensaja de éxito si se realiza correctamente. +

````
echo "$IP $DOMINIO" | sudo tee -a "/etc/hosts"

echo "Dominio '$DOMINIO' añadido con la IP '$IP' a /etc/hosts."
````

![image](https://github.com/user-attachments/assets/abd2e3ca-1e14-4157-b20b-93fa1a9f0bf1)

Para comprobarlo solo debemos de ejecutarlo con la sintaxis correcta.

![image](https://github.com/user-attachments/assets/8b2595f1-442d-4bc9-b333-d0a60dfdd16d)

Me saltó un error en la línea uno, porque puse la # después de la !.

## Script para crear una página web

Para este script lo voy ha realizar dentro de una función, para poder 

````
pagina() {
    TITULO=$1
    CABECERA=$2
    MENSAJE=$3
````
asd

````
  sudo tee "/var/www/html/pagina_web.html" <<< <!DOCTYPE html>
<html>
<head>
    <meta charset="UTF-8">
    <title>$TITULO</title>
</head>
<body>
    <h1>$CABECERA</h1>
    <p>$MENSAJE</p>
</body>
</html>

    echo "La página web ha sido creada en /var/www/html/pagina_web.html"
}
````
asd

````
if [ $# -ne 3 ]; then
    echo "Uso: $0 titulo cabecera mensaje"
    exit 1
fi
````
asd

````
pagina "$1" "$2" "$3"
````
![image](https://github.com/user-attachments/assets/169d1e40-23d2-430a-8149-738a163381cc)

