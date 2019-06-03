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

En este trabajo trataremos de crear VLANES para crear conexión a internet con cuatro equipos, 2 en la misma VLAN con IP´s diferentes mediante la conexión del hEX con el hAP, este último actúa como switch aunque de WIFI.

### Dispositivos

Vamos a utilizar dos **artilugios:**

**-hEX:** Es un enrutador de cinco puertos para ubicaciones donde no se requiere conectividad inalámbrica.

**-hAP:** Es el dispositivo inalámbrico para el hogar u oficina con el cual usaremos para crear y dar conexión, por ejemplo, al móvil.

### Winbox

**Winbox** es una pequeña aplicación que nos permite la administración de Mikrotik RouterOS usando una interfaz gráfica.

### Configuración hEX
En el primer puerto  lo conectaremos directamente a Internet a través de la roseta de la clase. Después lo enlazaremos con el hAP en el puerto 3. Finalmente, en el puerto 5, lo conectaremos con el equipo para que lo pueda detectar y así poder configurarlo.

Entraremos al **hEX** mediante la MAC(si no tiene IP puesta) con el Winbox.
Antes que nada, en el hEX, entraremos a las diferentes interfaces que tiene el dispositivo. En la pestaña **"Interface"** deberemos configurar distintas VLANES, en esta ocasión pondremos las IP´s mediante **"pool"** ¿de 1.0 y 2.0 en la interfaz 3 cuya conexión es el hAP.? [IMAGENES VLAN].
Una vez creadas, nos iremos a la configuración de esas propias VLANES, le pondremos la siguiente:
[IMAGENES CONFIGURACIÓN VLAN 10 Y VLAN 20]

Una vez realizadas las VLANES, nos dirigiremos a configurar el **"Bridge"**. Nos dirigiremos a la pestaña del **"Bridge"** y crearemos 2 para las VLANES que hemos creado [IMAGEN PESTAÑA DEL BRIDGE, BRIDGE]
A continuación nos dirigiremos a la pestaña **"Ports"** para configurar la salida de las VLANES creadas anteriormente.[IMAGEN PESTAÑA DEL PORT, BRIDGE]

Una vez terminado lo anterior, iremos a **"Addresses list"** en la opción **"Addresses"** para configurar las direcciones IP.
En el hEX(ya que en el hAP va a ser diferente), pondremos las IP´s [IMAGEN IP´s DE hEX]

Respecto al DHCP, crearemos un servidor en el hEX(es diferente en el hAP) para dar conexión IP a los equipos separados por las VLANES con las **"pools"** correspondientes [IMÁGENES SERVIDOR DHCP DEL hEX]   

### Configuración hAP
En la configuración del hAP en comparación con la del hEX, lo único que cambia es la pestaña de **"adresses"** y el **"servidor DHCP"**.
En la pestaña de las direcciones, cambiaremos la IP respecto al hEX ya que aquí daremos la IP que tendrán los distintos PC´s en la interfaz de la VLAN correspondiente.

En la parte del servidor DHCP, la diferencia que ha de tener el hAP respecto al hEX, es que no se monta el servidor DHCP.

Nombrar también que el puerto que enlaza el hEX y el hAP, tendrán que estar los dos en modo **"trunk"**
