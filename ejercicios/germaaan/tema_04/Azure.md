## Instalar la herramienta para trabajar desde línea de comandos para tu sistema operativo.

La opción más fácil para instalar el cliente de línea de comandos de Azure es como un paquete NPM.

```
sudo npm install -g azure-cli
```

![eje01_img01](https://dl.dropboxusercontent.com/s/wfs6hrfl17o9lo4/eje01_img01.png)

Para poder usarlo, primero tenemos que configurar nuestra cuenta de Azure, descargando e importando nuestras credenciales antes que cualquier otra cosa.

```
azure account download
azure account import cuenta.publishsettings
rm cuenta.publishsettings
```

![eje01_img02](https://dl.dropboxusercontent.com/s/3zsthqdrs1amhpa/eje01_img02.png)

Lo siguiente es crear una cuenta de almacenamiento en dónde se guardarán nuestras máquinas virtuales; además, debemos configurar el cliente para que trabaje sobre esa cuenta de almacenamiento.

```
azure account list
azure storage account create germaaancc --type LRS --location "Central US"
azure storage account keys list germaaancc
export AZURE_STORAGE_ACCOUNT=germaaancc
export AZURE_STORAGE_ACCESS_KEY={CLAVE}
```

![eje01_img03](https://dl.dropboxusercontent.com/s/88sqxku5pni2x0h/eje01_img03.png)

## Crear una máquina virtual en Azure.

Para crear una máquina virtual primero tenemos que conocer las imágenes de sistemas operativos que hay disponibles, en este caso vamos a instalar un sistema Ubuntu Server 15.10 64 bits, así que hacemos una consulta sobre las imágenes disponibles restringiendo el resultado a este sistema concreto. Una vez que sepamos el identificador de la imagen a instalar, podremos crearla.

```
azure vm image list | grep Ubuntu_DAILY_BUILD-wily-15_10
azure vm create germaaancc b39f27a8b8c64d52b05eac6a62ebad85__Ubuntu_DAILY_BUILD-wily-15_10-amd64-server-20160123-en-us-30GB --location "Central US" --vm-size Small --ssh --userName germaaan --password {PASSWORD}
```

![eje02_img01](https://dl.dropboxusercontent.com/s/v6rle4qpa5gi7v3/eje02_img01.png)

## Obtener la lista de máquinas.

Si la máquina virtual se ha creado correctamente debería aparecer en el listado de máquinas virtuales de nuestra cuenta. Vemos la máquina ha sido creada correctamente, pero como no ha sido iniciada ninguna vez, su estado de funcionamiento es desconocido.

```
azure vm list
```

![eje03_img01](https://dl.dropboxusercontent.com/s/zkzv3ouhx5a54wk/eje03_img01.png)

## Ejecutar nuestra máquina desde CLI.

Ahora solo queda arrancar la máquina virtual. Una vez que termine de arrancar su estado habrá pasado a preparada.

```
azure vm start germaaancc
```

![eje04_img01](https://dl.dropboxusercontent.com/s/9k6qoo1lalpbfgu/eje04_img01.png)

## Apagar nuestra máquina desde CLI.

También podemos apagar la máquina desde el cliente, pasando a un estado detenida.

```
azure vm shutdown germaaancc
```

![eje05_img01](https://dl.dropboxusercontent.com/s/jo74ucaegf8lyoh/eje05_img01.png)
