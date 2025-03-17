# techsupp0rt1 (thm)

Empezamos con un nmap de los puertos y parece que tenemos: ssh, servidor http, samba
![alt text](image.png)



**Apache**

En el servidor apache está la página por defecto 

![alt text](image-1.png)

Tiene un directorio que es `test` y otro que es `wordpress`

![alt text](image-2.png)

`/test`

Se puede ver un sitio con muchos avisos 

![alt text](image-3.png)

`/wordpress`

Se ve una página 

![alt text](image-5.png)

Tiene estos directorios

![alt text](image-4.png)

El más interesante es el `/wp-admin` y sale el tipico logeo en wordpress

**Samba**

En principio había empezado con el servidor apache pero como no encontré nada , voy a mirar lo primero de todo el samabclient y luego voy a la web

Se puede ver un direcotrio que se llama `websvr`
![alt text](image-7.png)

Vemos que hay un enter.txt y pone lo siguiente

![alt text](image-6.png)

Parece que hay un directorio llamado `/subrion` y a parte da credenciales que parecen del wordpress

Pone que está hecha con la magia por lo que despues de buscar mucho , en cyberchef hay para decodificar por magic 

![alt text](image-8.png)

Se ve esto `Scam2021`

En /subrion no sale nada solo el robots.txt

![alt text](image-9.png)

COn los datos de este he visto el /panel que tiene un login y nos vmaos a intentar logear con las credenciales de antes

![alt text](image-10.png)

Me logeo y sale esto y tenemos que el cms es `Subrion CMS v 4.2.1`

![alt text](image-11.png)

Buscamos su sploit
![alt text](image-12.png)

y lo explotamos

searchsploit -m php/webapps/49876.py

![alt text](image-14.png)

![alt text](image-13.png)

Se puede ver abajo que hay un suuario que se llama 

scamsite:x:1000:1000:scammer,,,:/home/scamsite:/bin/bash

Miramos en wordpress 

![alt text](image-15.png)

Se puede ver usuario y contraseña en el wp-config.php

![alt text](image-16.png)

Voy a intentar loegarme con eso en wordpress

![alt text](image-17.png)

No te deja por lo que vamos a probar por ssh

![alt text](image-18.png)

Con sudo -l se puede ver el payload y luego ejecutamos esto para ser root y ver la root.txt 

![alt text](image-19.png)