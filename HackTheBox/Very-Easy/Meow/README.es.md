# Meow
[![English](https://img.shields.io/badge/English-blue.svg)](README.md) [![Español](https://img.shields.io/badge/Español-green.svg)](README.es.md)

## Dificultad: Muy Fácil

![logo](img/logo.png)

Empiezo con un ping:

```
ping -c 1 10.129.129.152
```

![ping](img/1.png)

Hago un escaneo rápido con nmap y lo guardo en un txt:

```
sudo nmap -sS -sV -sC -T4 -O 10.129.129.152 -oN nmap.txt
```

![nmap](img/2.png)

Pruebo a logearme con telnet directamente como root. Es una máquina very easy al fin y al cabo, igual funciona.

```
telnet 10.129.129.152
```

![telnet](img/3.png)

Ha sido muy fácil, por algo es la máquina introductoria a Hack The Box, ahora simplemente hay que buscar la flag.

```
ls
cat flag.txt
```

![flag](img/4.png)

Resuelta.