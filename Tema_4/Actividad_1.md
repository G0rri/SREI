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

asd
```
sudo docker images
```
![image](https://github.com/user-attachments/assets/3823c721-91f0-4358-b95d-99f79c3c26ab)

asd
```
git clone https://github.com/docker/getting-started-app.git
```
![image](https://github.com/user-attachments/assets/b15c84d6-2ce2-4fb9-be96-41eb7a1e6549)

asd
```
FROM node:lts-alpine
WORKDIR /app
COPY . .
RUN yarn install --production
CMD ["node", "src/index.js"]
EXPOSE 3000
```
![image](https://github.com/user-attachments/assets/a04e7874-0d96-4058-94d2-44fb8c883578)

asd
```
docker build -t getting-started .
```
![image](https://github.com/user-attachments/assets/14b06930-da75-4f01-9137-f9f79baa19f4)

asd
```
docker run -d -p 127.0.0.1:3000:3000 getting-started
```
![image](https://github.com/user-attachments/assets/e18bfb27-b9ed-4373-b182-731dab65922b)

asd

![image](https://github.com/user-attachments/assets/e6034e7d-6ed2-4227-a5a9-da8b6f57b962)

asd
```
sudo docker login -u <usuario>
```
![image](https://github.com/user-attachments/assets/e7e9d75b-ac1e-4833-a89e-9ac22f5885a7)
