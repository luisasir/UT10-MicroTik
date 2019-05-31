# Trabajo Microtik

## Índice

<ul>
  
<li type="disc">Dispositivos.</li>

<li type="disc">WinBox.</li>

<li type="disc">Configuración hEX</li>

<li type="disc">Configuración hAP</li>

<li type="disc">Verificación</li>

</ul>

### Dispositivos

Vamos a utilizar dos **artefactos:**

**-hEX:** Es un enrutador de cinco puertos para ubicaciones donde no se requiere conectividad inalámbrica.

**-hAP:** Es el dispositivo inalámbrico para el hogar u oficina con el cual usaremos para crear y dar conexión, por ejemplo, al móvil

### Winbox

**Winbox** es una pequeña aplicación que nos permite la administración de Mikrotik RouterOS usando una interfaz gráfica.

### Configuración hEX
En el primer puerto  lo conectaremos directamente a Internet a través de la roseta de la clase. Después lo enlazaremos con el hAP en el puerto 3. Finalmente, en el puerto 5, lo conectaremos con el equipo para que lo pueda detectar y así poder configurarlo.

Entraremos al **hEX** mediante la MAC(si no tiene IP puesta) con el Winbox.
Seguidamente iremos a la pestaña de **"IP"**, después, "Adresses". Aquí configuraremos la dirección IP junto a las rutas que tendrá el Router. 
![Screenshot](https://i.ibb.co/0YC4G5b/HEX-IP-Y-ROUTE.png)
Donde la dirección **192.168.104.0** será la dirección del propio instituto.
La dirección **192.168.3.0** será la dirección hacia el equipo en el que estará conectado.
La dirección **192.168.1.0** será la del **hAP**.

Luego realizaremos los saltos necesarios mostrados en la imagen.

### Configuración hAP
En el primer puerto del **hAP** lo enlazaremos con el **hEX**.
En cuanto a la configuración, entraremos mediante la MAC respecto a **hEX** ya que se reconocen entre sí por estar conectadas.
Lo conectaremos a través del puerto de internet.
Para poder acceder a este mediante el **hEX**(ya que no tenemos la IP), necesitaremos entrar mediante la MAC cuya opción es **ROMmon**
En la configuración del **hAP**, primero, configuraremos su IP:
![Screenshot](https://i.ibb.co/HKqRTcF/HAP-IP.png)

Donde la dirección **192.168.1.0** es la que le daremos para conectar con el **hEX** y la **2.0**, la utilizaremos para dar conexión WIFI luego.

Y respecto a las **rutas:**
![Screenshot](https://i.ibb.co/J7j3nX1/HAP-ROUTE.png)

En realidad, sólo haría falta la primera ruta respecto a la segunda.
Luego pondremos a la **192.168.1.0**, a la **192.168.2.0** y a la **192.168.104.0**.

Ahora procederemos a crear el servidor DHCP:

![Screenshot](https://i.ibb.co/b5wnSgF/DHCP-SERVER.png)

Lo configuraremos en el bridge como muestra la imagen.

**IP POOL:**

![Screenshot](https://i.ibb.co/RymLrgB/IP-POOL.png)

Ahora procederemos a configurar la seguridad del Wireless:

![Screenshot](https://i.ibb.co/Zgp5m4g/wlan.png)

En la anterior imagen tocaremos más que nada donde pone "Mode" a "ap bridge", luego en el SSID pondremos el nombre que tendrá la conexión Wifi.
Al finalizar, nos dirigiremos a la pestaña **"Advanced Mode"**:

![Screenshot](https://i.ibb.co/hs82f82/VISHIPROFILE.png)

Una vez dentro, pondremos el nombre, el tipo de autenticación y la contraseña. Al acabar tendremos que clickar en **"Apply"**.

### Verificación

Para verificar que tenemos internet en el equipo conectado directamente al **hEX**, realizaremos un tracert para ver las rutas por las que va hasta poder llegar a conectarse:

![Screenshot](https://i.ibb.co/zGhc23V/tracert-8-8-8-8-pc.png)

En la anterior foto podemos ver los diferentes saltos que se realizan.

A continuación, haremos la prueba del Wifi mediante móviles. 
Primero activaremos la opción Wifi, luego buscaremos el SSID con su correspondiente clave que le hemos puesto anteriormente.

En la siguiente foto se podrá observar un registro de usuarios que se han conectado:

![Screenshot](https://i.ibb.co/kcM7fz8/DCHP-MOVIL.png)

Para finalizar, realizamos algunas capturas de un dispositivo móvil conectado a la **red** creada haciendo un **tracert**:

Estas son las características de la **red**:

![Screenshot](https://i.ibb.co/tsY34x1/IMG-20190522-WA0011.jpg)
![Screenshot](https://i.ibb.co/NjfQ8ks/IMG-20190522-WA0012.jpg)

Y esta es el recorrido que hace:
![Screenshot](https://i.ibb.co/PgV5c7D/IMG-20190522-WA0010.jpg)

## Vídeo
### Por último, mostrar el [vídeo](https://www.youtube.com/watch?v=CtbPDUnQNMk&feature=youtu.be) realizado a modo de tutorial.
