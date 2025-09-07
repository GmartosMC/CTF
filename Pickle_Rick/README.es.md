# Pickle Rick

[![English](https://img.shields.io/badge/English-blue.svg)](README.md) [![Español](https://img.shields.io/badge/Español-green.svg)](README.es.md)

![logo](img/logo.webp)

Este es un CTF de nivel fácil, dónde tenemos que comprometer un servidor web y encontrar tres banderas.

Empiezo haciendo un ping para comprobar que tenemos conexión con el servidor:

![Ping](img/ping.webp)

Tenemos conexión. Además, como el ttl es cercano a 64, sabemos que el objetivo es una máquina Unix, probablemente un Linux.

Accedo a la web con el navegador:

![Página de Inicio](img/inicio.webp)

Podemos ver que usa el protocolo HTTP, por tanto, el servidor probablemente esté usando el puerto 80. Vamos a analizar el código fuente de la página:

![Usuario](img/usuario.webp)

Encontramos el nombre de usuario en un comentario. No hay nada más a simple vista, vamos a buscar directorios ocultos con **Gobuster**, especificando que busque también archivos php, html y txt.

```bash
gobuster dir -w /usr/share/wordlists/dirbuster/directory-list-2.3-medium.txt -u http://10.10.12.39 -x php,html,txt
```

![Comando Gobuster](img/gobuster.webp)

Hay varios directorios ocultos. Particularmente interesantes son robots.txt y login.php. Vamos a robots.txt:

![robots.txt](img/robots.txt.webp)

Hay un texto extraño que no forma parte de un fichero robots.txt normal. Tal vez sea la contraseña. Lo guardaré.

Ahora vamos a login.php, y efectivamente está el portal de login. Pruebo el usuario y contraseña que encontramos:

![Login Portal](img/portal.webp)

¡Funciona! Ya tenemos acceso al servidor. Tenemos una terminal en la que podemos usar comandos. Usaré **pwd** para ver el directorio actual:

![pwd](img/pwd.webp)

Ahora **ls** para listar el contenido del directorio:

![ls](img/ls.webp)

Ahí está uno de los ingredientes. Intento leerlo con **cat** pero ese comando está bloqueado. Intento usar **nano** pero también está bloqueado. Pruebo con **less** y funciona:

![Bandera 1](img/flag1.webp)

Ya tenemos el primer ingrediente. Ahora leo el contenido de clue.txt:

![pista](img/pista.webp)

Tenemos una pista, nos indica que busquemos en el sistema de archivos. Pruebo a ver que hay en /home. Hay dos directorios, uno llamado Rick y otro llamado ubuntu. Busco en el de rick y encuentro el segundo ingrediente:

![Rick](img/rick.webp)

Lo leo con **less**, pero como hay un espacio tenemos que **escaparlo**:

![Bandera 2](img/flag2.webp)

Busqué en /home/ubuntu pero no había nada relevante. Pruebo si puedo escalar privilegios con **sudo** y funciona, ni siquiera necesito contraseña, pudiendo mirar en /root:

![root](img/root.webp)

Ahora lo leo con **less:**

![bandera3](img/flag3.webp)

Y con esto ya tenemos todos los ingredientes y hemos completado la máquina:

![fin](img/fin.webp)
