# Meow
[![English](https://img.shields.io/badge/English-blue.svg)](README.md) [![Español](https://img.shields.io/badge/Español-green.svg)](README.es.md)

## Difficulty: Very Easy

<img src="img/logo.png" alt="Alt Text" width="200">

I start with a ping:

```
ping -c 1 10.129.129.152
```

![ping](img/1.png)

Now I do a quick scan with nmap and save it into a txt file:

```
sudo nmap -sS -sV -sC -T4 -O 10.129.129.152 -oN nmap.txt
```

![nmap](img/2.png)

Because it's a very easy machine, I try to login with the root user by telnet.

```
telnet 10.129.129.152
```

![telnet](img/3.png)

It was very easy, it's the introductory machine to Hack The Box for a good reason, now I just search the flag:

```
ls
cat flag.txt
```

![flag](img/4.png)

Solved.