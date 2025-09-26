# Fawn
[![English](https://img.shields.io/badge/English-blue.svg)](README.md) [![Español](https://img.shields.io/badge/Español-green.svg)](README.es.md)

## Difficulty: Very Easy

<img src="img/logo.png" alt="Alt Text" width="200">

I start using nmap to enumerate the ports:

```
sudo nmap -sS -sV -sC -n --min-rate 5000 -p- 10.129.203.92 -oA scan
```

![nmap](img/1.png)

Anonymous login is enabled. Si I do it to see what can I get:

```
ftp 10.129.203.93
user: anonymous
```

![login FTP](img/2.png)

When it ask for a Password. I just type Enter

I check my path, list the directories, I see the flag and download it:

```
pwd
ls -a
get flag.txt
```

![Obtener la Flag](img/3.png)

Finally, I log out of the FTP and read the flag:

```
cat flag.txt
```

![flag](img/4.png)