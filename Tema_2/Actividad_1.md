# DNS Caching & Fordwarding Server

Actualizamos primero los paquetes que estén desactualizados.
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

Una vez abierto el archivo quitamos todo los comentarios, y nos debrá quear una cosa así.
```
options {
        directory "/var/cache/bind";

        dnssec-validation auto;

        auth-nxdomain no;    # conform to RFC1035
        listen-on-v6 { any; };
};
```
![image](https://github.com/user-attachments/assets/7c67e008-f14f-42ad-9c65-2fff5f698db4)

Encima de options, deberemos de crear un nuevo bloque acl con el nombre que queramos, en este caso goodclients. Aquí dentro añadiremos que dispositivos tendrán acceso a esta DNS.
```
acl goodclients {
    10.6.0.78/24;
    localhost;
    localnets;
};
```
Luego, dentro de options añadimos estas lineas que nos permitirán aplicar las lineas de acl.
```
 recursion yes;
    allow-query { goodclients; };
```
![image](https://github.com/user-attachments/assets/5811bce2-7612-4b2c-aaaf-fdba30e11099)

## Configuramos el DNS como reenviador

Dentro de options creamos un nuevo bloque para añadir las IP recursivas que están en nuestra DNS. El only sirve para que se ejecuten solo estas IPs,
```
forwarders {
                8.8.8.8;
                8.8.4.4;
        };
        forward only;
```
![image](https://github.com/user-attachments/assets/3bcbc29b-8920-419f-a3be-e8403111d70f)

Estas 2 últimas líneas sirven para evitar los posibles fallos de error.
```
dnssec-enable yes;
dnssec-validation yes;
```
![image](https://github.com/user-attachments/assets/c0e0e627-2771-4428-81b6-9c9f65299344)

Para comprobar que todo ha salido bien, primero lo analizamos sintácticamente por si hay algún error.
```
sudo named-checkconf
```
Luego reiniciamos el paquete bind9.
```
sudo systemctl restart bind9
```
Y lo permitimos.
```
sudo ufw allow Bind9
```
```
sudo journalctl -u bind9 -f
```
![image](https://github.com/user-attachments/assets/5b51d275-fff0-4dd0-83a7-b538f4aa8d4e)

Para comprobar que funciona, lo hacemos en una maquina cliente en Windows con este comando:
```
nslookup www.google.com 10.4.0.139
```
![image](https://github.com/user-attachments/assets/b99f299a-0e45-4beb-add6-ca3adb108138)

Donde la IP es la de la máquina con el DNS configurado.
