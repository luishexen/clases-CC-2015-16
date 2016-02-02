**Instalar docker.**

Siguiendo el proceso de instalación de la página oficial de docker para la [instalación en ubuntu](https://docs.docker.com/v1.8/installation/ubuntulinux/) necesitamos ejecutar el siguiente comando para obtener la última versión de docker e instalarla ( en modo root ).

```
curl -sSL https://get.docker.com/ | sh
```

A continuación podemos verificar mediante ```sudo docker run hello-world``` que la instalación se ha realizado correctamente. Se mostrará una imagen de prueba lanzada en un contenedor.

![docker](https://i.gyazo.com/4e0c2973f2754e7f9d9c802072d8a880.png)
>Figura 1. Lanzando imagen de test para verificar la correcta instalación.
