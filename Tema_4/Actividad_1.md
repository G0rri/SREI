## Instalación de Docker

Primero actualizamos ubuntu
```
sudo apt update
sudo apt install apt-transport-https ca-certificates curl gnupg lsb-release
```
![image](https://github.com/user-attachments/assets/91e4d404-494a-4a1d-a75f-33faed990474)

![image](https://github.com/user-attachments/assets/cad553ad-24b8-4d57-86b9-6d44e858fbcc)

Con el siguiente comando añadimos la clave para luego poder descargar el repositorio que contiene docker:
```
curl -fsSL https://download.docker.com/linux/debian/gpg | sudo gpg --dearmor -o /usr/share/keyrings/docker-archive-keyring.gpg
```
![image](https://github.com/user-attachments/assets/19691a2d-5c05-47a8-bd9a-f535c30644fc)

Añadimos el repositorio que contiene docker con:
```
echo "deb [arch=$(dpkg --print-architecture) signed-by=/usr/share/keyrings/docker-archive-keyring.gpg] https://download.docker.com/linux/debian $(lsb_release -cs) stable" | sudo tee /etc/apt/sources.list.d/docker.list > /dev/null
```
![image](https://github.com/user-attachments/assets/ada6cdf0-8422-4c1a-a708-14195dc36c19)

Volvemos a actualizar los repositorios y los actualizamos:
```
sudo apt update
sudo apt install docker-ce docker-ce-cli containerd.io docker-compose-plugin
```
![imagen](https://github.com/user-attachments/assets/eeff7e67-c81b-41c7-b0b5-779ed9d18939)

Descargamos las politicas de docker:
```
apt-cache policy docker-ce
```
![image](https://github.com/user-attachments/assets/28946553-4e70-407e-8c50-65cc6df6c57e)

Y nos disponemos a instalar docker:
```
sudo apt install docker-ce
```
![image](https://github.com/user-attachments/assets/82cfb995-c4df-4441-b766-39f292f08c57)

Vemos el estado de docker, para ver si está activo o no con:
```
sudo systemctl status docker
```
![image](https://github.com/user-attachments/assets/d41892c9-8993-4ef8-9f97-2c31882b588f)

Y para poder utilizar docker con este usuario, usamos este comando y también visualizaremos su versión.
```
sudo usermod -aG docker $USER
su - $USER
docker --version
```
![image](https://github.com/user-attachments/assets/1deb8d02-fcd9-449c-b747-3661d606ed3a)
