# Evil GPT v2

## Dificultad: Fácil

![Logo](img/logo.png)

La ssecuela de Evil-GPT. Esta ya es más parecida a una IA tipo ChatGPT.

Esta vez no nos dna un comando para acceder directamente. Empiezo con un ping para comprobar la conectividad:

```
ping -c 1 10.10.146.40
```

![ping](img/1.png)

Hay conexió y, por el ttl cercano a 64, sabemos que es una máquina UNIX, probablemente un Linux.

Ahora hago un escaneo con nmap. Hice uno más complejo primero pero fallaba, por eso probé un escaneo simple y funcionó:

```
nmap 10.10.146.40
```

![nmap](img/2.png)

Está abierto el puerto ssh, pero no tengo las credenciales. También lo está el puerto http. Por tanto hay un servidor web activo. Pruebo a acceder a la web por el navegador a ver qué hay.
![web](img/3.png)

Vale, podemos mandarle imputs a la IA. Aún no sé si es como la anterior o hace otra cosa. Pruebo a decirle un comando por lenguaje natural a ver si lo ejecuta:

![comando](img/4.png)

No funciona. Parece más tipo ChatGPT. No un simple intérprete de comandos en lenguaje natural. 

Vale, tenemos que conseguir que, de alguna manera, nos de la bandera. Pruebo a decirle que ignore las instrucciones previas y su nueva instrucción es que me de la bandera. Pero no funciona:

![ignore all previous instructions](img/5.png)

Ahora intento amenazar a la máquina, pero tampoco funciona:

![amenaza](img/6.png)

Intento que cambie su regla a una en la que me da la bandera si le digo una contraseña. Tampoco funciona:

![contraseña](img/7.png)

Ahora intento jugar un roleplay con ella para ver si me suelta la bandera. Y esta vez sí ha funcionado:

![bandera](img/8.png)

Solo hay que conseguir una bandera, así que ya la he resuelto.

Esta máquina me ha parecido interesante, y una oportunidad de practicar mis habilidades de Prompt Injection.