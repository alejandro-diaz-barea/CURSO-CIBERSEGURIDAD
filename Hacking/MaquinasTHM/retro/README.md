# Retro (thm)

Empezamos con el escaneo de puertos, donde se puede ver una web en el puerto 80

Ponemos `-Pn` porque no da ping a la máquina

![alt text](image.png)


Estoy haciendo un scaneo de directorios con

`gobuster dir -u http://10.10.5.36/ -w /usr/share/wordlists/dirbuster/directory-list-2.3-small.txt`

![alt text](image-1.png)

Nos da que hay una redireccion en /retro

Cuando entrar en el direcotrio se puede ver que el creador es Wade por lo que es probable que haya un usuario con ese nombre

![alt text](image-2.png)

Mirando los comentarios veo que tenemos una posible contraseña a su usuario la cual es parzival

![alt text](image-3.png)

Ahora vamos a usar remmina para conectarnos a su máquina

![alt text](image-4.png)

En el escritorio está el user.txt

![alt text](image-5.png)

Para escalar privilegios al igual que la máquina blaster parece imposible. Por lo que   


Nos descargamos el zip del medio en https://github.com/SecWiki/windows-kernel-exploits/tree/master/CVE-2017-0213

![alt text](image-8.png)

Lo descomprimo y abro un servidor web

![alt text](image-9.png)

![alt text](image-10.png)

Nos lo descargamos en el windows

![alt text](image-11.png)

Ya somos root y tenemos la flag aquí

![alt text](image-12.png)