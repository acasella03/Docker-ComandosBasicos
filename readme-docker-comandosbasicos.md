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
1. Descarga la imagen 'ubuntu y comprueba que está en tu equipo 

        Comando:            $ docker run ubuntu

        Para comprobar:     $ docker image ls
        
        La salida por consola es:

        REPOSITORY    TAG       IMAGE ID       CREATED        SIZE
        oraclelinux   9-slim    b88613e03d35   3 days ago     103MB
        **ubuntu        latest    c6b84b685f35   4 weeks ago    77.8MB**
        bash          latest    3c04497fad88   6 weeks ago    13.9MB
        hello-world   latest    9c7a54a9a43c   4 months ago   13.3kB

Como se puede observar en la línea marcada, se comprueba que existe la imágen


2. Crea un contenedor sin ponerle nombre. ¿está arrancado? Obtén el nombre

        Comando:        $ docker run -i -t  ubuntu:latest bash

        La salida por consola es:

        root@55c10eaa19d3:/# 

        Para comprobar si está arrancado y su nombre:  $ docker ps

        La salida por consola es:

         CONTAINER ID   IMAGE           COMMAND   CREATED           STATUS      PORTS       NAMES
         55c10eaa19d3   ubuntu:latest   "bash"    3 minutes ago     Up3minutes              flamboyant_napier