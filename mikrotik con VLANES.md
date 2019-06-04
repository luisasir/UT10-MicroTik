# Trabajo Microtik y VLANES.

## Índice

<ul>
  
<li type="disc">Objetivos.</li>
  
<li type="disc">Dispositivos.</li>

<li type="disc">WinBox.</li>

<li type="disc">Configuración hEX</li>

<li type="disc">Configuración hAP</li>

<li type="disc">Verificación</li>

</ul>
### Objetivos

En este trabajo trataremos de crear VLANES para crear conexión a internet con cuatro equipos, 2 en la misma VLAN con IP´s diferentes mediante la conexión del hEX con el hAP, este último actúa como switch aunque de WIFI aunque en el programa **Packet tracer** no nos permita diferenciarlo.

### Dispositivos

Vamos a utilizar dos **artilugios:**

**-hEX:** Es un enrutador de cinco puertos para ubicaciones donde no se requiere conectividad inalámbrica.

**-hAP:** Es el dispositivo inalámbrico para el hogar u oficina con el cual usaremos para crear y dar conexión, por ejemplo, al móvil.

### Winbox

**Winbox** es una pequeña aplicación que nos permite la administración de Mikrotik RouterOS usando una interfaz gráfica.

### Configuración hEX
En el primer puerto  lo conectaremos directamente a Internet a través de la roseta de la clase. Después lo enlazaremos con el hAP en el puerto 3. Finalmente, en el puerto 5, lo conectaremos con el equipo para que lo pueda detectar y así poder configurarlo.

Primero, entraremos al **hEX** mediante la MAC(si no tiene IP puesta) con el Winbox.
Antes que nada, en el hEX, accederemos a las diferentes interfaces que tiene el dispositivo. 
En la pestaña **"Interfaces"** deberemos configurar las dos VLANES, que vamos a crear en el ethernet 2. ![Screenshot](https://i.ibb.co/865w5kV/11-interfaces-hex.png)

Una vez realizadas las VLANES, nos dirigiremos a configurar el **"Bridge"**. Nos dirigiremos a la pestaña del **"Bridge"** y crearemos 2 para las VLANES que hemos creado. ![Screenshot](https://i.ibb.co/BKS0YwG/13-bridge-hex.png)

A continuación nos dirigiremos a la pestaña **"Ports"** para configurar la salida de las VLANES creadas anteriormente. ![Screenshot](https://i.ibb.co/yFtV4vw/14-bridge-2-hex.png)

Una vez terminado lo anterior, iremos a **"Addresses list"** en la opción **"Addresses"** para configurar las direcciones IP.
Pondremos las IP´s **192.168.10.1** y **192.168.20.1** enlazandolas con las distintas VLANES que hemos creado para crear la conexión. ![Screenshot](https://i.ibb.co/dWMPzFf/12-address-hex.png)

Una vez finalizado el punto anterior, nos dirigiremos a poner las rutas en la opción **"Route List""**:
![Screenshot](https://i.ibb.co/z4cwcMD/19-ip-routing-hex.png)

Respecto al DHCP, crearemos un servidor en el hEX para dar conexión IP a los equipos separados por las VLANES con las **"pools"** correspondientes, su configuración será: 
En la pestaña **DHCP**:
![Screenshot](https://i.ibb.co/gj0NSSj/17-dhcp-server-hex.png)

![Screenshot](https://i.ibb.co/tYBnR0h/18-dhcp-config-hex.png)

También deberemos de configurar las distinas **pools** para indicar en qué **IP** a que **IP** pueden estar, así que pondremos, en **pool 10,* de la **10.5 hasta la 10.100** y en **pool 20** de la **20.5 hasta la 20.100**:

![Screenshot](https://i.ibb.co/ww7SPhb/16-DHCP-pool-hex.png)


### Configuración hAP
En la configuración del hAP, conectaremos, en el puerto de internet, con el hEX.
Entraremos con el **Winbox** mediante la MAC, respecto a **hEX**, ya que se reconocen entre sí por estar conectadas.
En la pestaña **"Interfaces"** deberemos configurar distintas VLANES, al igual que el hEX, configuraremos las dos VLANES a crear en el ethernet 2 junto con un **"WLAN 1"** para el **Wifi**.
![Screenshot](https://i.ibb.co/k604J7B/02-interface-hap.png)

Una vez configurado lo anterior, nos iremos al **Bridge**.

Al igual que en el hEX, creamos dos para las VLANES creadas.
![Screenshot](https://i.ibb.co/wStfgLG/03-bridge-hap.png)

A continuación nos dirigiremos a la pestaña **"Ports"** para configurar la salida de las VLANES creadas anteriormente junto con el WLAN.

![Screenshot](https://i.ibb.co/JtXZ0kW/04-bridge-2-hap.png)

Ahora iremos a **"Addresses list"** en la opción **"Addresses"** para configurar las direcciones IP.
Pondremos las IP´s **192.168.10.2** y **192.168.20.2** enlazandolas con las distintas VLANES que hemos creado para que los dos equipos cojan esa misma IP.
![Screenshot](https://i.ibb.co/CtXTzNR/01-address-hap.png)

En el siguiente paso configuraremos las diferentes rutas:
![Screenshot](https://i.ibb.co/C8DNc5R/09-ip-routing-hap.png)

A continuación configuraremos el servidor DHCP que tendrá el dispositivo hAP.
En esta ocasión lo haremos por y para la conexión **Wifi**, crearemos otra nueva dirección (**192.168.30.0**).
En la pestaña **DHCP**:
![Screenshot](https://i.ibb.co/3psKX4D/07-dhcp-server.png)

En la pestaña **Networks**:
![Screenshot](https://i.ibb.co/FmjLLQ2/08-dhcp-config-hap.png)

Para crear el pool(lo crearemos de la **192.168.30.5** a la **192.168.30.100**):
![Screenshot](https://i.ibb.co/GJyqgDD/06-dhcp-pool-hap.png)

### Aclaraciones
**El puerto que enlaza el hEX y el hAP, tendrán que estar los dos en modo "trunk"**

**La NAT se hace de forma autmática en los dispisitivos "Miktrotik"**

### Verificación
Finalmente, nos conectaremos desde el ordenador que tiene IP **192.168.20.100** y realizaremos el comando **tracert** a **www.google.com**:
![Screenshot](https://i.ibb.co/dttvMCT/pingaso-y-tracert.png)

Por último, accederemos al SSID **Wifi** creado desde un dispositivo móvil y haremos un **tracert** a **google** (8.8.8.8):

Información de la red:

![Screenshot](https://i.ibb.co/ZmrSXNf/IMG-20190604-WA0021-resized.jpg)

Y el tracert:

![Screenshot](https://i.ibb.co/S5Nx199/IMG-20190604-WA0020-resized.jpg)

## Vídeo
### Por último, mostrar el [vídeo](https://www.youtube.com/watch?v=CtbPDUnQNMk&feature=youtu.be) realizado a modo de tutorial.
