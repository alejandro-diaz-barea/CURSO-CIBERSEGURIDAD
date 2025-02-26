# Kenobi (thm)

Empezamos con un escaneo básico de los puertos
![alt text](image.png)

Con este nmap vemos que hay 3 carpetas compartidas de samba
![](image-1.png)

POdemos logearnos como anonimo y hacer un ls y se ve un archivo que se llama log.txt

```bash
smbclient //10.10.82.34/anonymous
```

![alt text](image-2.png)

Se puede ver infromacion como

![alt text](image-3.png)

y el puerto es el 21 

![alt text](image-4.png)

El puerto 111 estaba abierto y thm nos explica que es un RPC y hay que usar este nmap 

```bash
nmap -p 111 --script=nfs-ls,nfs-statfs,nfs-showmount 10.10.82.34
```

![alt text](image-5.png)

Se ve que el mount esta en /var

Vemos aqui la version de FTP 

![alt text](image-6.png)

Tiene 4 exploits esta version

![alt text](image-7.png)

Obtener la versión de ProFTPd con netcat y ejecutar los comandos para copiar la clave privada 

![alt text](image-9.png)


Crear un direcotrio en nuestra máquina y montar el direcotrio en remoto 

![alt text](image-10.png)

Listar los archivos en `/var/tmp`

![alt text](image-11.png)

Descargar la clave privada a mi máquina

![alt text](image-12.png)

Conectarnos a kenobi por ssh

![alt text](image-13.png)

Flag

![alt text](image-14.png)


Buscando los tipos de archivos del sistema con el comando que dice thm , no se cual es el comando que no concuerda por lo que chatgpt me ha dicho que el que no cuadra es el `menu` 

![alt text](image-15.png)

Estas son las opciones que trae

![alt text](image-16.png)
![alt text](image-17.png)
![alt text](image-18.png)

Se ponen estos comanods :

![alt text](image-19.png)
![alt text](image-20.png)

Somos root

La flag esta en /root/root.txt

![alt text](image-21.png)