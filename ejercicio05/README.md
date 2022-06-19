## HEALTHCHECK

Esta instrucción de Dockerfile sirve para ejecutar un comando que mediante su exit-code, marque a nuestro container
como "healthy" o "unhealthy". Estos estados corresponden a los exit-codes 0 y 1 del comando ejectuado, respectivamente.
La instrucción tiene reintentos y tiempos de espera por defecto, que pueden ser modificados, tales
como intervalo de tiempo y cantidad de intentos antes de desistir si se tiene un exit-code distinto de cero.
Si se usa HEALTHCHECK, la información puede ser vista con ```docker ps```o ```docker inspect```.
En la primera se ve en la columna STATUS, y en la segundo en la key 'Status' del json.
Además del tipo de estos healthy o unhealthy, existe el estado 'Starting', que indica que el comando de chequeo no terminó con
todos sus reintentos y tiempos configurados.


## ONBUILD

La instrucción ONBUILD permite agregar otras instrucción que se va a ejecutar cuando la imagen es usada como base para otro build.
El Dockerfile que use una imagen base con la instrucción ONBUILD, ejecuta implícitamente estas instrucciones declaradas, como si estuvieran
en el mismo Dockerfile luego de la instrucción FROM.
Cualquier instrucción excepto otra ONBUILD, FROM, y MAINTAINER pueden ser registradas en ONBUILD.

Esto es útil en el caso que se quiera usar una imagen base para armar otras imágenes, evitando boilerplate de copy/paste.

## VOLUME

Crea un mount-point con el nombre especificado. Este mount-point va a contener volúmenes montados externamente, desde el host que core el container
u otros containers. Para que sea portable, no se puede declarar el directorio a montar desde el host en el Dockerfile. Éste directorio se indica al
momento de crear o correr un container.


## Referencias:

- https://docs.docker.com/engine/reference/builder/#healthcheck
- https://docs.docker.com/engine/reference/builder/#onbuild
- https://docs.docker.com/engine/reference/builder/#volume
- https://docs.docker.com/develop/develop-images/dockerfile_best-practices/#onbuild
- https://docs.docker.com/develop/develop-images/dockerfile_best-practices/#volume
