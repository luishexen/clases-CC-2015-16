**Crear a partir del contenedor anterior una imagen persistente con commit.**

Mientras el contenedor se encuentra en funcionamiento mediante el comando ```docker ps -notrunc``` podemos obtener su ID.

![imagen](https://i.gyazo.com/6b472e66a438f27a7dd38811706da362.png)
> Figura 1. Obtención del ID del contenedor.

Usamos el ID anterior para hacer commit y de ese modo la imagen sea persistente.

```sudo docker commit <ID> centosnginx```

![imagen2](https://i.gyazo.com/57c6a24b325343a153a663127848a674.png)
> Figura 2. Creando una imagen persistente.



