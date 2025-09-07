# Lo-Fi
[![English](https://img.shields.io/badge/English-blue.svg)](README.md) [![Español](https://img.shields.io/badge/Español-green.svg)](README.es.md)

## Dificultad: Fácil

![logo](img/logo.png)

Tenemos que encontrar solo una bandera.

Empiezo haciendo un ping:

```
ping -c 1 10.10.164.237
```

![1](img/1.png)

Tenemos conectividad. Por el ttl cercano a 64, sabemos que es un Linux. Sé que se puede modificar el valor, pero las máquinas fáciles en TryHackMe no lo hacen. 

Uso nmap para ver los puertos abiertos y guardo el resultado en nmap.txt:

```
nmap -p- -sV -sC -sS 10.10.164.237 -oN nmap.txt
```

![nmap](img/2.png)

Tiene el puerto 22 (SSH) y el puerto 80 (HTTP). Como no tengo las credenciales para entrar por SSH. Vamos a ver qué hay en la web mientras uso gobuster.

![web](img/3.png)

Gobuster no me ha encontrado nada que pueda usar. Solo ha encontrado las distintas páginas que ya tenemos enlazadas en el index de todos modos.

Acceso a una de las páginas enlazadas y me llama la atención la URL:

![url](img/4.png)

Creo que lo que va detrás del = es la dirección interna que busca la petición GET HTTP que mandamos. Vamos a interceptar una petición con Burp Suite para verlo.

Abro Burp Suite, configuro el proxy en el navegador:

![proxy](img/5.png)

Activo el Intercept y mandamos la petición:

![petición](img/6.png)

Sí, creo que después del = busca la ruta al archivo cuando le mandas la petición, vamos a intentar un Path Traversal. El más básico de ir para atrás con ../

![Path Traversal](img/7.png)

![passwd](img/8.png)

Funciona. No hay ningún usuario que tenga un /home. Llegados a este punto, intenté ver si me dejaba intentar contraseñas por ssh, con el usuario root, pero me negaba el acceso sin siquiera dejarme introducir contraseñas. 

Intenté leer /etc/shadow con el mismo Path Traversal para ver si somos root. Salió una página en blanco lo que significa que no somos root y no nos deja leerlo.

Sabiendo que hay que encontrar una bandera, seguramente se llame algo como flag.txt flag1.txt user.txt root.txt (en caso de que esté en /root) suele ser alguna de esas. Y estará, o en el directorio base del servidor, en algún /home pero en este caso no porque no hay usuarios con /home. En / o en /root. 

Como no tenemos root, lo quehe hecho a sido probar estas combinaciones menos la de /root manualmente. Hasta que la encontré en /flag.txt

![flag](img/9.png)
