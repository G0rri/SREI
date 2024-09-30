# Actividad 0.2 - UDP and TCP: Comparison of Transport Protocols
https://www.youtube.com/watch?v=Vdc8TCESIg8

## Diferencias entre udp y tcp? (min 2:46 y 4:15)
El protocolo UDP no revisa si los datos enviados se han enviado correctamente, y por lo tanto el envío no tiene garantías pero es más rápido en la entrega. En cuanto el TCP, se asegura de que los datos se van ha enviar ya que comprueba si ha llegado, y si no realiza de nuevo el envío. Por culpa de esto también es más lento por tener que hacer todas estás comprobaciones.

## ¿Qué aplicaciones usan tcp?  
HTTP, SMTP, POP, IMAP, SSH etc..

## ¿Qué aplicaciones usan udp?
Tales como DNS, DHCP, VoIP, o los juegos que necesitan de internet.

## ¿Qué capa almacena el puerto?
La capa que almacena el puerto es la de transporte, ya que se comunica entre los dispositivos y las aplicaciones.

## ¿Qué capa almacena la dirección IP?
La capa que almacena la dirección de IP es la de red, ya que la IP va por internet entre las distintas redes.

## ¿Qué es three-way handshake?
Es un proceso que se utiliza en TCP para conectarse a un servidor, y como su propio nombre indica hay 3 pasos:
SYN: El emisor envía una parte del mensaje al servidor para iniciar la conexión con este.
SYN-ACK: El servidor te devuelve la parte del mensaje al emisor.
ACK: El emisor envía una especie de  recibo al servidor para que la conexión se complete.
