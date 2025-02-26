## Instalación de Docker

asd
```
 sudo apt-get update
 sudo apt-get install ca-certificates curl gnupg
```
![image](https://github.com/user-attachments/assets/91e4d404-494a-4a1d-a75f-33faed990474)

![image](https://github.com/user-attachments/assets/e5da1ea2-83d6-4154-ad01-9a48af4fda66)

asd
```
 sudo install -m 0755 -d /etc/apt/keyrings
 curl -fsSL https://download.docker.com/linux/debian/gpg | sudo gpg --dearmor -o /etc/apt/keyrings/docker.gpg
 sudo chmod a+r /etc/apt/keyrings/docker.gpg
```
![image](https://github.com/user-attachments/assets/c9ff57fc-e8a7-4acc-bcaf-18b2c9605579)
