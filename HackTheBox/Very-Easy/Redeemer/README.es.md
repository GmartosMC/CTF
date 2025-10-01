# Redeemer
[![English](https://img.shields.io/badge/English-blue.svg)](README.md) [![Español](https://img.shields.io/badge/Español-green.svg)](README.es.md)

## Dificultad: Muy Fácil

<img src="img/logo.png" alt="Alt Text" width="200">

Hago un ping para verificar la conexión:

```
ping -c 1 10.129.178.183
```

![ping](img/1.png)

Hago la enumeración con nmap:

```
sudo nmap -sS -sV -sC -Pn -n -p- --min-rate 5000 10.129.178.183 -oA resultado
```

![nmap](img/2.png)

Soo encuentra el servicio de redis. Intento conectar sin contraseña:

![redis](img/3.png)

No sabía nada de redis, así que busqué lo básico de cómo funciona, y me levó un rato de ensayo y error entenderlo y poder sacar la flag:

![flag](img/4.png)