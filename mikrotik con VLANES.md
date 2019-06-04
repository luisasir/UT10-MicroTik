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
En la pestaña **"Interfaces"** deberemos configurar distintas VLANES, en esta ocasión pondremos las IP´s de 10.0 y 20.0 y configuraremos las dos VLANES a crear en el ethernet 2. ![Screenshot](https://i.ibb.co/865w5kV/11-interfaces-hex.png)

Una vez realizadas las VLANES, nos dirigiremos a configurar el **"Bridge"**. Nos dirigiremos a la pestaña del **"Bridge"** y crearemos 2 para las VLANES que hemos creado. ![Screenshot](https://i.ibb.co/BKS0YwG/13-bridge-hex.png)

A continuación nos dirigiremos a la pestaña **"Ports"** para configurar la salida de las VLANES creadas anteriormente. ![Screenshot](https://i.ibb.co/yFtV4vw/14-bridge-2-hex.png)

Una vez terminado lo anterior, iremos a **"Addresses list"** en la opción **"Addresses"** para configurar las direcciones IP.
Pondremos las IP´s **192.168.10.1** y **192.168.20.1** enlazandolas con las distintas VLANES que hemos creado. ![Screenshot](https://i.ibb.co/dWMPzFf/12-address-hex.png)

Una vez finalizado el punto anterior, nos dirigiremos a poner las rutas en la opción **"Route List""**:
![Screenshot](https://i.ibb.co/z4cwcMD/19-ip-routing-hex.png)

Respecto al DHCP, crearemos un servidor en el hEX para dar conexión IP a los equipos separados por las VLANES con las **"pools"** correspondientes, su configuración será: 
![Screenshot](https://i.ibb.co/gj0NSSj/17-dhcp-server-hex.png)

![Screenshot](https://i.ibb.co/tYBnR0h/18-dhcp-config-hex.png)

También deberemos de configurar las distinas **pools** para indicar en qué **IP** a que **IP** pueden estar, así que pondremos, en **pool 10,* de la **10.5 hasta la 10.100** y en **pool 20** de la **20.5 hasta la 20.100**:

![Screenshot](https://i.ibb.co/ww7SPhb/16-DHCP-pool-hex.png)


### Configuración hAP
En la configuración del hAP, conectaremos, en el puerto de internet, con el hEX.
Entraremos con el **Winbox** mediante la MAC, respecto a **hEX**, ya que se reconocen entre sí por estar conectadas.
En la pestaña **"Interfaces"** deberemos configurar distintas VLANES, al igual que el hEX, pondremos las IP´s de 10.0 y 20.0 y configuraremos las dos VLANES a crear en el ethernet 2.

En la parte del servidor DHCP, la diferencia que ha de tener el hAP respecto al hEX, es que no se monta el servidor DHCP.

**Nombrar también que el puerto que enlaza el hEX y el hAP, tendrán que estar los dos en modo "trunk"**

### Verificación
