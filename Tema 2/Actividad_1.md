# DNS Caching & fordwarding DNS Server

Actualizamos primero los paquetes que estén desactializados.
```
sudo apt-get update
```
![image](https://github.com/user-attachments/assets/670142c9-1d93-45a1-bcd4-29164ee4933a)

Instalamos los bind del DNS.
```
sudo apt-get install bind9 bind9utils bind9-doc
```
![image](https://github.com/user-attachments/assets/63116c57-227d-4975-9a45-1ed49ca0ad62)

## Configuramos el caché del servidor DNS

Ahora nos desplazamos al directorio donde está el bind instalado.
```
cd /etc/bind
```
![image](https://github.com/user-attachments/assets/ffbdab26-480a-424b-a6f2-f1f1320ddd0f)

Para el caché del DNS solo debemos de modificar este archivo
```
sudo nano named.conf.options
```
![image](https://github.com/user-attachments/assets/a3044f7c-7164-4fa6-bbd8-d7c49a27369c)

asd
```
options {
        directory "/var/cache/bind";

        dnssec-validation auto;

        auth-nxdomain no;    # conform to RFC1035
        listen-on-v6 { any; };
};
```
![image](https://github.com/user-attachments/assets/7c67e008-f14f-42ad-9c65-2fff5f698db4)

asd
```
acl goodclients {
    10.6.0.78/24;
    localhost;
    localnets;
};
```
```
 recursion yes;
    allow-query { goodclients; };
```
![image](https://github.com/user-attachments/assets/5811bce2-7612-4b2c-aaaf-fdba30e11099)

asd
