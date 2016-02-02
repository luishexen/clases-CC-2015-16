# Ejercicio 8
## Instalar docker.

```
sudo apt-key adv --keyserver hkp://p80.pool.sks-keyservers.net:80 --recv-keys 58118E89F3A912897C070ADBF76221572C52609D
echo 'deb https://apt.dockerproject.org/repo ubuntu-wily main' | sudo tee /etc/apt/sources.list.d/docker.list
```

![Ejercico8_1](http://googledrive.com/host/0B5Yam2FWqtZPZGJWT1JHNzI1Uzg/Ejercicio8_1.png)

```
sudo apt-get update
sudo apt-get install linux-image-extra-$(uname -r) docker-engine
```

Vamos a comproba que está todo correcto y que corre.

```
sudo service docker start
```

![Ejercico8_2](http://googledrive.com/host/0B5Yam2FWqtZPZGJWT1JHNzI1Uzg/Ejercicio8_2.png)