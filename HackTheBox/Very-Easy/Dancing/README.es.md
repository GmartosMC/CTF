# Dancing
[![English](https://img.shields.io/badge/English-blue.svg)](README.md) [![Español](https://img.shields.io/badge/Español-green.svg)](README.es.md)

## Dificultad: Muy Fácil

<img src="img/logo.png" alt="Alt Text" width="200">

Primero lanzo un nmap para enumerar los puertos:

```
sudo nmap -sS -sV -sC -Pn -n --min-rate 5000 10.129.164.151 -oA scan
```
![nmap](img/1.png)

Enumero los recursos compartidos del SMB:

```
smbclient -L \\\\10.129.164.151\\
```

![Listar SMB](img/2.png)

Intento acceder sin contraseña a cada uno de los recursos compartidos, finalmente funciona con WorkShares:

```
smbclient \\\\10.129.164.151\\WorkShares
```

![Acceso](img/3.png)

Busco en los distintos directorios hasta que encuentro la bandera:

![Buscar flag](img/4.png)


Me desconecto del SMB y leo la bandera:

![flag](img/5.png)
