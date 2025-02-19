## Creación de VPC

Lo primero será crear una VPC (Virtual Private Cloud), para ello buscamos VPC y le damos a donde pone crear.

![image](https://github.com/user-attachments/assets/98199e9b-89bc-4393-8c51-62b3a33e8249)

A continuación empezamos con la creación de la VPC y más. Le asignamos un nombre, y que el bloque del CIDR IPv4 sea 10.2.0.0/16. Por el resto seguimos como en la imagen.

![image](https://github.com/user-attachments/assets/c61bc710-b12f-4bb5-958e-ecb8d33aceb1)

Ahora debemos especificar en cada subred el tamaño e IP que queremos, para el resto lo dejamos como en la imagen.

![image](https://github.com/user-attachments/assets/9a7e380e-1716-4bd5-9228-bc0c4ce8aba2)

Esperamos a que implemente y cree todo lo que le acabamos de especificar.

![image](https://github.com/user-attachments/assets/8750de95-0d45-4c03-b4b9-afb36ee6c856)

Y como vemos nos saldrá algo así.

![image](https://github.com/user-attachments/assets/a3edd080-7842-48ef-843c-c7deaf818ca4)

## Creación de EC2 y Firewall

asd

![image](https://github.com/user-attachments/assets/0e13c838-eefb-4d3a-aa10-c6d374c0431e)

asd

![image](https://github.com/user-attachments/assets/d22e1f2e-7910-408a-ab59-66ce32794a54)

asd

![image](https://github.com/user-attachments/assets/00c9023d-512f-4309-bfce-372c226f5d42)

asd

![image](https://github.com/user-attachments/assets/6c1985ae-4186-42eb-81c0-e2b7b0f751fd)

asd

![image](https://github.com/user-attachments/assets/0daab50c-0523-4d21-a9e1-14c2ee7fd110)

asd

![image](https://github.com/user-attachments/assets/fde51ff0-aff2-4724-bdbd-3ef78db7e924)

## Instalación de Apache y PHP
Lo primero es actualizar el ubuntu junto a todos sus paquetes y repositorios.

![image](https://github.com/user-attachments/assets/87318902-d3ec-4662-8726-4f563d7606a8)

Ahora instalamos apache
```
sudo apt install apache2
```
![image](https://github.com/user-attachments/assets/63f29bc5-ff38-44d0-add6-2b44b63c3d14)

Ahora lo iniciamos y activamos.
```
sudo systemctl start apache2
sudo systemctl enable apache2
```
![image](https://github.com/user-attachments/assets/2f3fb676-1db4-45ce-aaab-c537c123c779)

Para comprobarlo, en un navegador ponemos la IP pública de la instancia.

![image](https://github.com/user-attachments/assets/0e529fcc-ac2f-4b76-bc09-9844a62921ef)

## Creación de la base de datos

## Implementación de EFS

## Instalación de Wordpress
