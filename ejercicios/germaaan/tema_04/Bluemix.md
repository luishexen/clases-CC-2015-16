## Crear una cuenta en Bluemix.

Nos creamos una cuenta en Bluemix desde su [página de registro](https://console.ng.bluemix.net/registration/). Cuando finalizemos el registro y activemos la cuenta, podremos acceder sin mayor problema. (Nota: por algún motivo, el acceso con Google Chrome produce algunos problemas, usar Mozilla Firefox).

![eje01_img01](https://dl.dropboxusercontent.com/s/infry89hy7m3bo1/eje01_img01.png)

## Desplegar una aplicación web sencilla (elige el lenguaje).

Primero descargamos e instalamos la línea de comandos de Cloud Foundry para poder trabajar con nuestra cuenta de Bluemix desde una terminal.

```
wget http://go-cli.s3-website-us-east-1.amazonaws.com/releases/v6.15.0/cf-cli-installer_6.15.0_x86-64.deb && sudo dpkg -i cf-cli-installer_6.15.0_x86-64.deb
```

![eje02_img01](https://dl.dropboxusercontent.com/s/76ulripgfan3eu6/eje02_img01.png)

Como aplicación de prueba vamos a usar la aplicación de prueba en **Node.js** que crea el paquete `express` como ejemplo de su funcionalidad. Después de instalar el generador (`express-generator`), creamos la aplicación (`prueba`).

```
sudo npm install -g express-generator
express prueba
```

![eje02_img02](https://dl.dropboxusercontent.com/s/6zedbebl98voj53/eje02_img02.png)

Nos desplazamos al directorio que se ha creado para la aplicación e instalamos todas las dependencias de la aplicación.

```
cd prueba && npm install
```

![eje02_img03](https://dl.dropboxusercontent.com/s/h2mwzbwzw7y4mcg/eje02_img03.png)

Ahora solo nos queda arrancar la aplicación.

```
DEBUG=prueba:* npm start
```

![eje02_img04](https://dl.dropboxusercontent.com/s/9ghkz1475wq09ci/eje02_img04.png)

Si accedemos a la dirección [http://localhost:3000](http://localhost:3000), deberíamos encontrarnos la aplicación funcionando.

![eje02_img05](https://dl.dropboxusercontent.com/s/cf88wyscdrnvhdt/eje02_img05.png)

Lo siguiente que vamos a hacer es deplegar la aplicación en **Bluemix**, para ello lo primero que tenemos que hacer es conectar con Bluemix mediante su API (importante que nos conectemos a la API de la región donde tenemos nuestra cuenta albergada, en este caso la región es **Reino Unido** así que la API es **eu-gb**). Una vez hayamos conectado, tendremos que iniciar sesión con nuestra cuenta, indicando además el nombre del espacio donde desplegar nuestra aplicación (`dev`).

```
cf api https://api.eu-gb.bluemix.net
cf login -u germaaan@gmail.com -o germaaan@gmail.com -s dev
```

![eje02_img06](https://dl.dropboxusercontent.com/s/ttxjxv5zatkukt5/eje02_img06.png)

Ahora desde el directorio de nuestra aplicación, la desplegamos con la orden `push`, indicando además la cantidad de memoria de la que dispondrá la aplicación (`512m`).

```
cf push germaaancc -m 512m
```

![eje02_img07](https://dl.dropboxusercontent.com/s/3p5i42hso8pkyl7/eje02_img07.png)

Cuando termine el despliegue de la aplicación, el cliente nos informará si este ha sido correcto, además de diversas propiedades del despliegue de nuestra aplicación de la que ahora la que más nos interesa es la dirección de acceso (`URL`).

![eje02_img08](https://dl.dropboxusercontent.com/s/hoqu3bu0t73dh7f/eje02_img08.png)

Para comprobar que el despliegue ciertamente ha sido exitoso, accedemos a la dirección que nos indicaba el cliente al finalizar el despliegue: [http://germaaancc.eu-gb.mybluemix.net](http://germaaancc.eu-gb.mybluemix.net).

![eje02_img09](https://dl.dropboxusercontent.com/s/iaui3wwwovll5e9/eje02_img09.png)

## Modifica y actualiza tu aplicación.

Modificamos los mensajes de la aplicación por unos típicos **"Hola Mundo"** y volvemos a ejecutar la aplicación para comprobar los cambios.

```
sed -i 's/Express/Hola Mundo/g' routes/index.js
sed -i 's/Welcome to #{title}/Aplicación de prueba para Cloud Computing/g' views/index.jade
DEBUG=prueba:* npm start
```

![eje03_img01](https://dl.dropboxusercontent.com/s/7l58sc1jpxzd5o1/eje03_img01.png)

La dirección de acceso local, sigue siendo [http://localhost:3000](http://localhost:3000).

![eje03_img02](https://dl.dropboxusercontent.com/s/07eg1j9hqm1gnjw/eje03_img02.png)

Desplegamos los cambios con el comando `push`.

```
cf push germaaancc
```

![eje03_img03](https://dl.dropboxusercontent.com/s/37nnen8z7p1jfmj/eje03_img03.png)

![eje03_img04](https://dl.dropboxusercontent.com/s/ytousgvxdd5rpe0/eje03_img04.png)

Y la aplicación modificada ya está desplegada y accesible en [http://germaaancc.eu-gb.mybluemix.net](http://germaaancc.eu-gb.mybluemix.net)

![eje03_img05](https://dl.dropboxusercontent.com/s/d25hho286265uiu/eje03_img05.png)

## Monitorízala durante el tiempo que está en ejecución.

Para ver las entradas de registro actuales de nuestra aplicación usaremos el comando `logs` con la opción `--recent`.

```
cf logs germaaancc --recent
```

![eje04_img01](https://dl.dropboxusercontent.com/s/lw3gp6utup4fdr5/eje04_img01.png)

## Opcional: crea una máquina virtual, y accede a ella para instalar y configurar un servidor web.

Antes de crear la máquina virtual, si no tenemos creado el par de claves para conexión SSH las creamos; si las tenemos creadas, simplemente las copiamos.

```
ssh-keygen -t rsa -b 4096 -C "germaaan@gmail.com"
xclip -sel clip < ~/.ssh/id_rsa.pub
```

El primer paso en la creación de una máquina virtual es acceder al panel de control de nuestra cuenta de Bluemix y pulsar el botón **"Ejecutar máquinas virtuales"**.

![eje05_img01](https://dl.dropboxusercontent.com/s/fj4zponuhhe1zvx/eje05_img01.png)

Lo siguiente es configurar las características de la máquina virtual, básicamente, el sistema operativo que se le va a instalar, el nombre de la máquina y el tamaño; también será importante añadir el archivo de nuestra clave SSH pública (pulsando el enlace **"Añadir clave"**). Una vez que todo esto esté listo, pulsamos el botón **"Crear"** para iniciar la creación de la máquina.

![eje05_img02](https://dl.dropboxusercontent.com/s/cua8nkgm4ssv71p/eje05_img02.png)

Cuando finalice la creación, nos encontraremos en el dashboard de la máquina virtual que acabamos de crear, donde se muestran su principales propiedades; particularmente nos interesan el nombre de usuario (que por defecto es **ibmcloud**) y la dirección IP pública para poder acceder a él (en este caso la IP es **159.122.255.218**).

![eje05_img03](https://dl.dropboxusercontent.com/s/4zin64691y86xzf/eje05_img03.png)

Ahora nos conectamos por SSH a la máquina virtual.

```
ssh ibmcloud@159.122.255.218
```

![eje05_img04](https://dl.dropboxusercontent.com/s/v5xijr1puz9vp2y/eje05_img04.png)

E instalamos el servidor **nginx**.

```
sudo apt-get install nginx
```

![eje05_img05](https://dl.dropboxusercontent.com/s/y870bxwsdip4x74/eje05_img05.png)

Como siempre, comprobamos que el servidor está funcionando correctamente.

```
sudo service nginx status
```

![eje05_img06](https://dl.dropboxusercontent.com/s/p1oipvw0rtjjkfk/eje05_img06.png)

Si accedemos a la dirección pública de nuestra máquina virtual, veremos como el servidor está funcionando a la perfección.

![eje05_img07](https://dl.dropboxusercontent.com/s/kvoihkfc80rvuoi/eje05_img07.png)

Lo último que deberemos hacer es eliminar la máquina virtual y borrar nuestra tarjeta de crédito de la cuenta de Bluemix para evitar cualquier tipo de recargo.

![eje05_img08](https://dl.dropboxusercontent.com/s/h4m4257xaxnk3xv/eje05_img08.png)
