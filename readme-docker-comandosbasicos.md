# Práctica: Docker - Comandos básicos
## Enunciado
La siguiente práctica es una lista de tareas que tenéis que hacer. Por cada tarea tenéis que ir poniendo los comandos utilizados y, brevemente, describir el proceso.

Utilizaremos la imagen de Ubuntu. Usa Visual Studio Code y Docker junto con esta imagen para seguir las siguientes instrucciones:

1. Descarga la imagen 'ubuntu y comprueba que está en tu equipo
2. Crea un contenedor sin ponerle nombre. ¿está arrancado? Obtén el nombre
3. Crea un contenedor con el nombre 'dam_ubu1'. ¿Como puedes acceder a él?
4. Comprueba que ip tiene y si puedes hacer un ping a google.com
5. Crea un contenedor con el nombre 'dam_ubu2'. ¿Puedes hacer ping entre los contenedores?
6. Sal del terminal, ¿que ocurrió con el contenedor?
7. ¿Cuanta memoria en el disco duro ocupaste?
8. ¿Cuanta RAM ocupan los contenedores? ¿Hay algún comando docker para saber esto?.

## Respuesta
1. - [x] Descarga la imagen 'ubuntu y comprueba que está en tu equipo 

        Comando:            $ docker run ubuntu

        Para comprobar:     $ docker image ls
        
        La salida por consola es:

        REPOSITORY    TAG       IMAGE ID       CREATED        SIZE
        oraclelinux   9-slim    b88613e03d35   3 days ago     103MB
        ubuntu        latest    c6b84b685f35   4 weeks ago    77.8MB
        bash          latest    3c04497fad88   6 weeks ago    13.9MB
        hello-world   latest    9c7a54a9a43c   4 months ago   13.3kB

> [!NOTE]
> Como se puede observar en la línea 2, se comprueba que existe la imágen.


2. - [x] Crea un contenedor sin ponerle nombre. ¿está arrancado? Obtén el nombre

        Comando:        $ docker run -i -t  ubuntu:latest bash

        La salida por consola es:

        root@55c10eaa19d3:/# 

        Para comprobar si está arrancado y su nombre:  $ docker ps

        La salida por consola es:

         CONTAINER ID   IMAGE           COMMAND   CREATED           STATUS      PORTS       NAMES
         55c10eaa19d3   ubuntu:latest   "bash"    3 minutes ago     Up3minutes              flamboyant_napier

> [!NOTE]
> Como se puede observar, se comprueba que que el nombre es **flamboyant_napier**.

3. - [x] Crea un contenedor con el nombre 'dam_ubu1'. ¿Como puedes acceder a él?

        Comando:        $ docker run --name dam_ubu1 -it ubuntu:latest

        Para acceder:   $ docker exec -it dam_ubu1 bash

4. - [x] Comprueba que ip tiene y si puedes hacer un ping a google.com

        Comando:        apt update
                        apt install net-tools
                        ifconfig

        Salida por consola:

        eth0: flags=4163<UP,BROADCAST,RUNNING,MULTICAST>  mtu 1500
        inet 172.17.0.2  netmask 255.255.0.0  broadcast 172.17.255.255
        ether 02:42:ac:11:00:02  txqueuelen 0  (Ethernet)
        RX packets 22770  bytes 29046627 (29.0 MB)
        RX errors 0  dropped 0  overruns 0  frame 0
        TX packets 11897  bytes 795269 (795.2 KB)
        TX errors 0  dropped 0 overruns 0  carrier 0  collisions 0

        lo: flags=73<UP,LOOPBACK,RUNNING>  mtu 65536
        inet 127.0.0.1  netmask 255.0.0.0
        loop  txqueuelen 1000  (Local Loopback)
        RX packets 0  bytes 0 (0.0 B)
        RX errors 0  dropped 0  overruns 0  frame 0
        TX packets 0  bytes 0 (0.0 B)
        TX errors 0  dropped 0 overruns 0  carrier 0  collisions 0

        Comando(ping):  apt install iputils-ping
                        ping www.google.com
        
        Salida por consola:

        64 bytes from mad07s10-in-f4.1e100.net (172.217.168.164): icmp_seq=1 ttl=110 time=15.4 ms
        64 bytes from mad07s10-in-f4.1e100.net (172.217.168.164): icmp_seq=2 ttl=110 time=16.6 ms
        64 bytes from mad07s10-in-f4.1e100.net (172.217.168.164): icmp_seq=3 ttl=110 time=15.9 ms
        64 bytes from mad07s10-in-f4.1e100.net (172.217.168.164): icmp_seq=4 ttl=110 time=15.8 ms
        64 bytes from mad07s10-in-f4.1e100.net (172.217.168.164): icmp_seq=5 ttl=110 time=15.0 ms
        64 bytes from mad07s10-in-f4.1e100.net (172.217.168.164): icmp_seq=6 ttl=110 time=15.5 ms
        64 bytes from mad07s10-in-f4.1e100.net (172.217.168.164): icmp_seq=7 ttl=110 time=15.7 ms
        64 bytes from mad07s10-in-f4.1e100.net (172.217.168.164): icmp_seq=8 ttl=110 time=15.8 ms
        64 bytes from mad07s10-in-f4.1e100.net (172.217.168.164): icmp_seq=9 ttl=110 time=15.2 ms
        64 bytes from mad07s10-in-f4.1e100.net (172.217.168.164): icmp_seq=10 ttl=110 time=15.8 ms
        64 bytes from mad07s10-in-f4.1e100.net (172.217.168.164): icmp_seq=11 ttl=110 time=16.0 ms
        64 bytes from mad07s10-in-f4.1e100.net (172.217.168.164): icmp_seq=12 ttl=110 time=15.7 ms
        64 bytes from mad07s10-in-f4.1e100.net (172.217.168.164): icmp_seq=13 ttl=110 time=15.8 ms
        64 bytes from mad07s10-in-f4.1e100.net (172.217.168.164): icmp_seq=14 ttl=110 time=18.5 ms
        .
        .
        .
> [!NOTE]
> Todos éstos comando deben ser dentro del contenedor **dam_ubu1**.<br>
> Para detener el ping a Google **Ctrol+c**.

5. - [x] Crea un contenedor con el nombre 'dam_ubu2'. ¿Puedes hacer ping entre los contenedores?

        Comando: $ docker run --name dam_ubu2 -it ubuntu:latest bash

        Comando(ping): ping 172.17.0.2
        Salida por consola:
        bash: ping: command not found

> [!NOTE]
> Todos éstos comando deben ser dentro del contenedor **dam_ubu2**.<br>
> En éste caso no funciona porque se debe actualizar e instalar las tools en **dam_ubu2**, ya que donde se hizo fue en el contenedor **dam_ubu1**.

        Comando(ping):  apt update
                        apt install iputils-ping
                        ping 172.17.0.2

        Salida por consola:
        PING 172.17.0.2 (172.17.0.2) 56(84) bytes of data.
        64 bytes from 172.17.0.2: icmp_seq=1 ttl=64 time=0.219 ms       
        64 bytes from 172.17.0.2: icmp_seq=2 ttl=64 time=0.114 ms
        64 bytes from 172.17.0.2: icmp_seq=3 ttl=64 time=0.113 ms
        64 bytes from 172.17.0.2: icmp_seq=4 ttl=64 time=0.111 ms
        64 bytes from 172.17.0.2: icmp_seq=5 ttl=64 time=0.118 ms
        64 bytes from 172.17.0.2: icmp_seq=6 ttl=64 time=0.111 ms
        64 bytes from 172.17.0.2: icmp_seq=7 ttl=64 time=0.120 ms
        64 bytes from 172.17.0.2: icmp_seq=8 ttl=64 time=0.119 ms
        64 bytes from 172.17.0.2: icmp_seq=9 ttl=64 time=0.116 ms
        64 bytes from 172.17.0.2: icmp_seq=10 ttl=64 time=0.112 ms
        64 bytes from 172.17.0.2: icmp_seq=11 ttl=64 time=0.042 ms
        64 bytes from 172.17.0.2: icmp_seq=12 ttl=64 time=0.099 ms
        64 bytes from 172.17.0.2: icmp_seq=13 ttl=64 time=0.058 ms
        64 bytes from 172.17.0.2: icmp_seq=14 ttl=64 time=0.061 ms
        64 bytes from 172.17.0.2: icmp_seq=15 ttl=64 time=0.116 ms
        64 bytes from 172.17.0.2: icmp_seq=16 ttl=64 time=0.116 ms
        .
        .
        .
> [!NOTE]
> Todos éstos comando deben ser dentro del contenedor **dam_ubu2**.<br>
> En éste caso si funciona porque se realizaron los comando de instalación en **dam_ubu2**.
> Para detener el ping **Ctrol+c**.

6. - [x] Sal del terminal, ¿que ocurrió con el contenedor?

        Comando: exit

> [!NOTE]
> El contenedor se cierra, pero no se borra, para comprobar que existe será con el siguiente comando:

        Comando: $ docker ps -a

        Salida por consola:
        CONTAINER ID   IMAGE           COMMAND       CREATED          STATUS                      PORTS     NAMES
        fb14ccd0adea   ubuntu:latest   "bash"        16 minutes ago   Exited (0) 10 seconds ago             dam_ubu2
        fa0d9a6d36a6   ubuntu:latest   "/bin/bash"   3 hours ago      Up 2 hours                            dam_ubu1
        3f2e58a2105b   ubuntu          "bash"        45 hours ago     Exited (137) 22 hours ago             ubi2
        241540ca4e5f   ubuntu          "bash"        45 hours ago     Exited (137) 18 hours ago             ubi1