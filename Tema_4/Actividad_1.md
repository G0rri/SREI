## Instalación de Docker

asd
```
 sudo apt update
 sudo apt install apt-transport-https ca-certificates curl software-properties-common
```
![image](https://github.com/user-attachments/assets/91e4d404-494a-4a1d-a75f-33faed990474)

![image](https://github.com/user-attachments/assets/cad553ad-24b8-4d57-86b9-6d44e858fbcc)

asd
```
curl -fsSL https://download.docker.com/linux/ubuntu/gpg | sudo apt-key add -
```
![image](https://github.com/user-attachments/assets/19691a2d-5c05-47a8-bd9a-f535c30644fc)

asd
```
sudo add-apt-repository "deb [arch=amd64] https://download.docker.com/linux/ubuntu focal stable"
```
![image](https://github.com/user-attachments/assets/ada6cdf0-8422-4c1a-a708-14195dc36c19)

asd
```
sudo apt update $$ sudo apt upgrade
```
![image](https://github.com/user-attachments/assets/fbe7b7b2-7b67-44fb-b51d-8dd6bcd4b88e)

asd
```
apt-cache policy docker-ce
```
![image](https://github.com/user-attachments/assets/28946553-4e70-407e-8c50-65cc6df6c57e)

asd
```
sudo apt install docker-ce
```
![image](https://github.com/user-attachments/assets/82cfb995-c4df-4441-b766-39f292f08c57)

asd
```
sudo systemctl status docker
```
![image](https://github.com/user-attachments/assets/d41892c9-8993-4ef8-9f97-2c31882b588f)

asd
```
sudo usermod -aG docker $USER
su - $USER
docker --version
```
![image](https://github.com/user-attachments/assets/1deb8d02-fcd9-449c-b747-3661d606ed3a)

## Tarea 2

asd
```
sudo docker run hello-world
```
![image](https://github.com/user-attachments/assets/fc23319e-fed9-459e-9ec3-e7793eea117d)

asd
```
sudo docker ps -a
```
![image](https://github.com/user-attachments/assets/176007a2-c2fa-485e-85bd-bd3dd8b68032)
