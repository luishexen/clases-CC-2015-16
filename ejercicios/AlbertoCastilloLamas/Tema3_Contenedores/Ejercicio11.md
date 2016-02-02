# Ejercicio 11
## Crear a partir del contenedor anterior una imagen persistente con commit.
Listamos los contenedores con sus ID y obtenemos su ID copmleto.

```
sudo docker ps -a --no-trunc
sudo docker inspect <ID_SEÑALADO>
```

![Ejercico11_1](http://googledrive.com/host/0B5Yam2FWqtZPZGJWT1JHNzI1Uzg/Ejercicio11_1.png)

Conociendo el ID completo del contenedor podemos crear una imagen persistente de nuestro docker.

```
docker commit <ID_SEÑALADO> nginx
docker images
```

![Ejercico11_2](http://googledrive.com/host/0B5Yam2FWqtZPZGJWT1JHNzI1Uzg/Ejercicio11_2.png)

![Ejercico11_3](http://googledrive.com/host/0B5Yam2FWqtZPZGJWT1JHNzI1Uzg/Ejercicio11_3.png)