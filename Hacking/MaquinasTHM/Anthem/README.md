# Anthem (thm)

Para empezar vemos que no se puede hacer ping, por lo debe de haber un firewall que lo prohiba. Vamos a poner en nmap `-Pn` para que ignore el ping y de por echo que existe el servidor

![alt text](image.png)

Luego he dejado un fuzeo con gobuster de los direcotrios que nos da lo siguiente

![alt text](image-7.png)

En el `/robots.txt` hay una potencial contraseña 

![alt text](image-1.png)

El cms obviamente es `umbraco`

El dominio es `Anthem.com`

![alt text](image-2.png)

Buscando el usuario me he encontrado una flag que igual nos sirve para despues.

![alt text](image-3.png)

Tambien me he encontrado otra flag en /authors

![](image-4.png)

He buscado el poema que le dedican al admin en google y pone que es de `Solomon Grundy`

![alt text](image-5.png)

En el primer blog pone `JD@anthem.com` pero ese parece que no es el correo del admin. Pero imagino que sera con ese dominio con las inicales en mayúsculas el correo del admin es `SG@anthem.com` ya que el de JD era Jane Doe

![alt text](image-6.png)

**Flag 1**
Inspeccionar en `/archive/we-are-hiring/`
![](image-9.png)

**Flag 2**

Buscando thm en el inspeccionar en `/archive/we-are-hiring/` estaba esta

![alt text](image-8.png)

**Flag 3**

`/authors` que hemos encontrado antes

**Flag 4**

`/archive/a-cheers-to-our-it-department/` que tambien hemos visto antes

Como tenemos usuario y contraseña vamos a usar remmina para conectarnos en remoto 

![alt text](image-10.png)

Con el usuario Solomon Grundy no funciona pero con las inicales si 

Nada más iniciarla sale un user.txt

![alt text](image-11.png)

Si en esta ruta le cambiamos los permisos en propertis->secure podemos ver la contraseña

![alt text](image-12.png)

Una vez que tenemos la contraseña y sabemos que el suaurio es Administrator pues vamos a crear otra conexión para escalar privilegios

![alt text](image-13.png)

y tenemos el root.txt 

![alt text](image-14.png)