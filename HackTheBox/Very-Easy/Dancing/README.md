# Dancing
[![English](https://img.shields.io/badge/English-blue.svg)](README.md) [![Español](https://img.shields.io/badge/Español-green.svg)](README.es.md)

## Difficulty: Very Easy

<img src="img/logo.png" alt="Alt Text" width="200">

I run nmap to enumerate the ports:

```
sudo nmap -sS -sV -sC -Pn -n --min-rate 5000 10.129.164.151 -oA scan
```
![nmap](img/1.png)

I enumerate the SMB shares

```
smbclient -L \\\\10.129.164.151\\
```

![Enumerate SMB](img/2.png)

I try to join without passwords to the shares, it works with WorkShares:

```
smbclient \\\\10.129.164.151\\WorkShares
```

![Join](img/3.png)

I search until I find the flag:

![Search flag](img/4.png)


I log out the SMB and read the flag:

![flag](img/5.png)
