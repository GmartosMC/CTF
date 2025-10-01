# Redeemer
[![English](https://img.shields.io/badge/English-blue.svg)](README.md) [![Español](https://img.shields.io/badge/Español-green.svg)](README.es.md)

## Difficulty: Very Easy

<img src="img/logo.png" alt="Alt Text" width="200">

I make a pin to test connection:

```
ping -c 1 10.129.178.183
```

![ping](img/1.png)

I run nmap to enumerate:

```
sudo nmap -sS -sV -sC -Pn -n -p- --min-rate 5000 10.129.178.183 -oA resultado
```

![nmap](img/2.png)

I only found redis. I try to connect without password:

![redis](img/3.png)

I didn't know anything about redis, so I searched the basics of how redis works, and it took me a bit of trial and error to understand it and be able to get the flag:

![flag](img/4.png)