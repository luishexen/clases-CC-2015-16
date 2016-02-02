# Ejercicio 3
## 1. Crear y ejecutar un contenedor basado en Debian.

```
sudo lxc-create -n container-test -t ubuntu
```

![Ejercico3_1](http://googledrive.com/host/0B5Yam2FWqtZPZGJWT1JHNzI1Uzg/Ejercicio3_1.png)

![Ejercico3_2](http://googledrive.com/host/0B5Yam2FWqtZPZGJWT1JHNzI1Uzg/Ejercicio3_2.png)

## 2. Crear y ejecutar un contenedor basado en otra distribución, tal como Fedora. Nota En general, crear un contenedor basado en tu distribución y otro basado en otra que no sea la tuya. Fedora, al parecer, tiene problemas si estás en Ubuntu 13.04 o superior, así que en tal caso usa cualquier otra distro. Por ejemplo, [Óscar Zafra ha logrado instalar Gentoo usando un script descargado desde su sitio, como indica en este comentario en el issue](https://github.com/IV-GII/GII-2013/issues/87#issuecomment-28639976).

```
sudo lxc-create -n fedoracaja -t fedora  -- -R 23
```