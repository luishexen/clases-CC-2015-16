**Instala LXC en tu versión de Linux favorita. Normalmente la versión en desarrollo, disponible tanto en GitHub como en el sitio web está bastante más avanzada; para evitar problemas sobre todo con las herramientas que vamos a ver más adelante, conviene que te instales la última versión y si es posible una igual o mayor a la 1.0.**

Instalamos lxc o bien mediante el repositorio de Github de modo que tendremos la última versión.

```
git clone https://github.com/lxc/lxc
cd lxc
sudo ./autogen.sh
sudo ./configure
sudo make
sudo make install
```

O bien usando el gestor de paquetes apt-get actualizado.

```sudo apt-get install lxc```

![lxc](https://i.gyazo.com/4e9a0f19b933ecf91ed490f3482c58f7.png)
> Figura 1. Lxc-checkconfig
