# Fawn
[![English](https://img.shields.io/badge/English-blue.svg)](README.md) [![Español](https://img.shields.io/badge/Español-green.svg)](README.es.md)

## Dificultad: Muy Fácil

<img src="img/logo.png" alt="Alt Text" width="200">

Empiezo usando nmap para enumerar los puertos de la máquina:

```
sudo nmap -sS -sV -sC -n --min-rate 5000 -p- 10.129.203.92 -oA scan
```

![nmap](img/1.png)

Vemos que el login como anónimo en el servidor FTP está habilitado. Por tanto voy a hacerlo a ver qué puedo conseguir

```
ftp 10.129.203.93
user: anonymous
```

![login FTP](img/2.png)

Cuando pide contraseña, simplemente pulso Enter.

Compruebo mi ruta, listo los directorios, veo que está la bandera y la descargo:

```
pwd
ls -a
get flag.txt
```

![Obtener la Flag](img/3.png)

Me deslogeo del FTP y leo el contenido de la bandera:

```
cat flag.txt
```

![flag](img/4.png)