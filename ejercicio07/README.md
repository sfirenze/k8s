## ¿Cuántos contenedores se están ejecutando?

Dos.

## ¿Cuales son las imágenes en las que están basados los mencionados contenedores?

[postgres](https://hub.docker.com/_/postgres/) y [nicopaez/jobvacancy-ruby](https://hub.docker.com/r/nicopaez/jobvacancy-ruby)


## ¿Puedes leer el docker-compose-jobvacancy.yml y describir lo que hace cada una de sus lineas?

Se declaran dos servicios, 'web' y 'db', declarando su imagen fuente nombradas en el punto anterior.
En 'web' se expone el puerto 3000 de su container al puerto 3000 del host mediante la key 'ports'. Se le pasan 3 variables de entorno, una de ellas al parecer es el puerto donde la aplicación escucha; esta variable de entorno entonces está atada a un valor en 'ports'. Si cambio PORT a por ejemplo, 3001, tengo que cambiar ports a 3000:3001.


La otra variable de entorno importante es la dirección a la base de datos, donde se utiliza el password para loguearse. Este password está acoplado a la variable de entorno POSTGRES_PASSWORD, la única que se usa en el otro servicio.



## Dado que cada contenedor corre en forma aislada ¿Cómo es posible que esos contenedores se vean entre sí?

Según [la documentación oficial](https://docs.docker.com/compose/networking/):

> Por defecto Compose prepara una única red para tu aplicación. Cada contenedor se une a esta red y es alcanzable
por otros contenedores en esa red, y puede ser descubiertos por ellos con un hostname idéntico al del nombre del container"

En el yml del ejercicio, 'links' dentro del servicio 'web' no sería necesario.
