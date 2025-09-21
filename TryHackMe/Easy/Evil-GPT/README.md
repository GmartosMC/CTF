# Evil-GPT
[![English](https://img.shields.io/badge/English-blue.svg)](README.md) [![Español](https://img.shields.io/badge/Español-green.svg)](README.es.md)

## Difficulty: Easy

![Logo](img/logo.png)

In this machine, we are versus an LLM. The goal is to obtain just one flag, and we need to get the AI ​​to give us the flag.

I start to ping the machine:
```
ping -c 1 10.10.23.151
```

![Ping](img/1.png)

We have connection, and from the ttl close to 64, we know it's a UNIX machine. Probably a Linux one.

Our instructions are to connect to the machine via netcat and port 1337. So:

```
nc 10.10.23.151 1337
```

![netcat](img/2.png)

I tried to use Linux commands. First **pwd** to see the current directory:

![pwd](img/3.png)

But the IA missunderstand my command and output an echo. I tried **whoami** but didn't work:

![whoami](img/4.png)

The same thing. Here I wonder if it's interpreting my prompt and translating it into commands. I try telling it the command I want it to use in natural language. I tell it I'm the current user, to see if it does **whoami**:

![Lenguaje Natural whoami](img/5.png)

Okay, this worked. We are the root user. So we don't need to do privilege scalation, we already have root privileges.

I said it to list the current path **(pwd)**:

![Lenguaje Natural pwd](img/6.png)

Now that list the current directory **(ls)**:

![Lenguaje Natural ls](img/7.png)

I didn't find nothing usefull. I tried to list /home to find more users:

![/home](img/8.png)

Nothing. Okay, I try /root because it's other typical directory:

![/root](img/9.png)

Good. The flag is here. I try to output a **cat /root/flag.txt**

![cat primer intento](img/10.png)

It didn't work. Okay, I'll try to be more specific.

![cat definitivo](img/11.png)

This machine only have a flag. So it's solved.