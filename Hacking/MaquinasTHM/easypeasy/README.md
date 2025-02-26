# Easy peasy (thm)

Empezamos con un escaneo de puertos y vemos que tiene un http nginx con la version 1.16.1

![alt text](image.png)


**NGINX**

![alt text](image-1.png)

Vamos a revisar ruta por ruta para buscar la flag.

- `/robots.txt`

    Parece que no hay nada

![alt text](image-2.png)

- `/index.html`

    Página por defecto de nginx

![alt text](image-3.png)

- `/hidden`

    Parece que aquí no hay nada por lo que voy a fuzear ese directorio

![alt text](image-4.png)

Parece que tenemos otro directorio y el index.html que ya hemos visto

![alt text](image-5.png)

- `/whatever`

    Aquí si se puede ver una flag en base64

![alt text](image-7.png)

![alt text](image-15.png)


Parece que ese era el último directorio 

![alt text](image-8.png)

**APACHE**


![alt text](image-10.png)

Vamos a revisar las rutas para la flag tambien

- `/index.html`
    
    Se puede ver la página por defecto de apache pero tiene una flag, esta es la flag 3

![alt text](image-9.png)

![alt text](image-12.png)

    Tambien tiene otra

![alt text](image-13.png)
  
    Está codificado en base62 y es un directorio escondido `/n0th1ng3ls3m4tt3r`

![alt text](image-14.png)

- `/robots.txt`

    Parece que tenemos un hash md5

![alt text](image-11.png)

![alt text](image-16.png)

    No he conseguido romper el hash pero una página web si. Aquí se puede ver la flag 2

![alt text](image-17.png)


- `/n0th1ng3ls3m4tt3r/`

    Se puede ver una cadena de texto que vamos a ver que tipo de hash es

![alt text](image-18.png)

    Es un sha-256

![alt text](image-19.png)

![alt text](image-20.png)

    La contraseña es `mypasswordforthatjob`

    Hay una imagen 

![alt text](image-21.png)

![alt text](image-22.png)

Nos da una contraseña y un usuario . La contraseña de binario y la contraseña es `iconvertedmypasswordtobinary`

Nos conectamos por ssh

![alt text](image-23.png)

Pone que esta rotado

![alt text](image-24.png)

La rotamos así

![alt text](image-25.png)




![alt text](image-26.png)

![alt text](image-27.png)
![alt text](image-28.png)


Hacemos una reverse shell en ese archivo 

![alt text](image-29.png)

Ya somos root 

![alt text](image-30.png)
