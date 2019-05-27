# Trabajo Microtik

## Índice

<ul>
  
<li type="disc">Dispositivos.</li>

<li type="disc">WinBox.</li>

<li type="disc">Configuración HeX</li>

<li type="disc">Configuración HaP</li>

<li type="disc">RommON</li>

</ul>

### Dispositivos

Vamos a utilizar dos **artefactos:**

**-HeX:** Es un enrutador de cinco puertos para ubicaciones donde no se requiere conectividad inalámbrica.

**-HaP:** Es el dispositivo inalámbrico para el hogar u oficina con el cual usaremos para crear y dar conexión, por ejemplo, al móvil

### Winbox

Winbox es una pequeña aplicación que nos permite la administración de Mikrotik RouterOS usando una interfaz gráfica

### Configuración HeX
En el primer puerto  lo conectaremos directamente a Internet a través de la roseta de la clase. Después lo enlazaremos con el HaP en el puerto 3. Finalmente, en el puerto 5, lo conectaremos con el equipo para que lo pueda detectar y así poder configurarlo.

Entraremos al HeX mediante la MAC(si no tiene IP puesta) con el Winbox.
Seguidamente iremos a la pestaña de "IP", después, "Adresses". Aquí configuraremos la dirección IP junto a las rutas que tendrá el Router. 
![Screenshot](https://i.ibb.co/0YC4G5b/HEX-IP-Y-ROUTE.png)
Donde la dirección 192.168.104.0 será la dirección del propio instituto.
La dirección 192.168.3.0 será la dirección hacia el equipo en el que estará conectado.
La dirección 192.168.1.0 será la del HaP.

Luego realizaremos los saltos necesarios mostrados en la imagen.

### Configuración HaP
En el primer puerto del HaP lo enlazaremos con el HeX.
En cuanto a la configuración, entraremos mediante la MAC respecto a HeX ya que se reconocen entre sí por estar conectadas.
Lo conectaremos a través del puerto de internet.
En la configuración del HaP, primero, configuraremos su IP:
![Screenshot](https://i.ibb.co/HKqRTcF/HAP-IP.png)

Donde la dirección 192.168.1.0 es la que le daremos para conectar con el HeX y la 2.0, la utilizaremos para dar conexión WIFI luego.

Y respecto a las rutas:
![Screenshot](https://i.ibb.co/J7j3nX1/HAP-ROUTE.png)

En realidad, sólo haría falta la primera ruta respecto a la segunda.
Luego pondremos a la 192.168.1.0, a la 192.168.2.0 y a la 192.168.104.0.

Ahora procederemos a crear el servidor DHCP:

![Screenshot](https://i.ibb.co/b5wnSgF/DHCP-SERVER.png)

Lo configuraremos en el bridge como muestra la imagen.

IP POOL:

![Screenshot](https://i.ibb.co/RymLrgB/IP-POOL.png)

Ahora procederemos a configurar la seguridad del Wireless:

![Screenshot](https://i.ibb.co/Zgp5m4g/wlan.png)

En la anterior imagen tocaremos más que nada donde pone "Mode" a "ap bridge", luego en el SSID pondremos el nombre que tendrá la conexión Wifi.
Al finalizar, nos dirigiremos a la pestaña "Advanced Mode":

![Screenshot](https://i.ibb.co/hs82f82/VISHIPROFILE.png)

Una vez dentro, pondremos el nombre, el tipo de autenticación y la contraseña. Al acabar tendremos que clickar en "Apply".

### Verificación

Para verificar que tenemos internet en el equipo conectado directamente al HeX, realizaremos un tracert para ver las rutas por las que va hasta poder llegar a conectarse:

![Screenshot](https://i.ibb.co/zGhc23V/tracert-8-8-8-8-pc.png)

En la anterior foto podemos ver los diferentes saltos que se realizan.

A continuación, haremos la prueba del Wifi mediante móviles. 
Primero activaremos la opción Wifi, luego buscaremos el SSID con su correspondiente clave que le hemos puesto anteriormente.

En la siguiente foto se podrá observar un registro de usuarios que se ha conectado:

![Screenshot](https://i.ibb.co/kcM7fz8/DCHP-MOVIL.png)

## Deployment

Add additional notes about how to deploy this on a live system

## Built With

* [Dropwizard](http://www.dropwizard.io/1.0.2/docs/) - The web framework used
* [Maven](https://maven.apache.org/) - Dependency Management
* [ROME](https://rometools.github.io/rome/) - Used to generate RSS Feeds

## Contributing

Please read [CONTRIBUTING.md](https://gist.github.com/PurpleBooth/b24679402957c63ec426) for details on our code of conduct, and the process for submitting pull requests to us.

## Versioning

We use [SemVer](http://semver.org/) for versioning. For the versions available, see the [tags on this repository](https://github.com/your/project/tags). 

## Authors

* **Billie Thompson** - *Initial work* - [PurpleBooth](https://github.com/PurpleBooth)

See also the list of [contributors](https://github.com/your/project/contributors) who participated in this project.

## License

This project is licensed under the MIT License - see the [LICENSE.md](LICENSE.md) file for details

## Acknowledgments

* Hat tip to anyone whose code was used
* Inspiration
* etc


