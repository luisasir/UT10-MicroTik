# Trabajo Microtik y VLANES.

## Índice

<ul>
  
<li type="disc">Dispositivos.</li>

<li type="disc">WinBox.</li>

<li type="disc">Configuración hEX</li>

<li type="disc">Configuración hAP</li>

<li type="disc">Verificación</li>

</ul>

### Dispositivos

Vamos a utilizar dos **artilugios:**

**-hEX:** Es un enrutador de cinco puertos para ubicaciones donde no se requiere conectividad inalámbrica.

**-hAP:** Es el dispositivo inalámbrico para el hogar u oficina con el cual usaremos para crear y dar conexión, por ejemplo, al móvil.

### Winbox

**Winbox** es una pequeña aplicación que nos permite la administración de Mikrotik RouterOS usando una interfaz gráfica.

### Configuración hEX
En el primer puerto  lo conectaremos directamente a Internet a través de la roseta de la clase. Después lo enlazaremos con el hAP en el puerto 3. Finalmente, en el puerto 5, lo conectaremos con el equipo para que lo pueda detectar y así poder configurarlo.

Entraremos al **hEX** mediante la MAC(si no tiene IP puesta) con el Winbox.
Antes que nada, en el hEX, entraremos a las diferentes interfaces que tiene el dispositivo. En la pestaña **"Interface"** 
Seguidamente iremos a la pestaña de **"IP"**, después, "Adresses". Aquí configuraremos la dirección IP junto a las rutas que tendrá el Router.
