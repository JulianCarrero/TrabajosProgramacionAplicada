# TrabajosProgramacionAplicada

# Repetidor de WIFI con Raspberry Pi
## ¿Que es un repetidor WIFI?
* Un repetidor WIFI es un dispositivo **electrónico** que permite ampliar la cobertura en la red inálambrica de internet; su función principal se basa en captar la señal de la red wifi ya instalada y ampliarla a sitios donde no haya una buena **señal** o cobertura.
![Repetidor WIFI con Raspberry Pi](https://pimylifeup.com/wp-content/uploads/2017/04/WiFiExtender-mini-watermark.jpg)
> Para desarrollar este proyecto serán necesarios...
## Lista de materiales
Según las indicaciones del fabricador:
> A continuación están todas las piezas que he utilizado para este tutorial de Raspberry Pi WiFi Extender, necesitarás dos dongles WiFi para poder completar este tutorial, al menos uno debe ser capaz de actuar como punto de acceso.
### Obligatorios | Necesarios
1. Raspberry Pi (modelo 2 o 3).
2. Tarjeta Micro SD o una tarjeta SD; esta solo es necesaria si se va a usar una versión antigua de la tarjeta Raspberry.
3. Fuente de alimentación.
4. Wifi dongle * 2 (La tarjera Raspberry Pi 3 tiene WiFi incorporado)
### Opcionales
* Caja o soporte de la tarjeta
## ¿Cómo configurar el repetidor?
Para configurar el repetidor WIFI con nuestra tarjeta Raspberry Pi Wifi Extender se recomienda (como se indica en la página web del desarrollador) usar el paquete _dnsmasq_; ya que actúa como nuestro servidor **DNS** y __DHCP__ para nuestras conexiones. También necesitaremos utilizar el paquete *hostapd*, este es el paquete que nos permitirá configurar uno de nuestros módulos Wi-Fi como punto de acceso o raíz.

**ACLARACIÓN**: _Recordar que para este proyecto es necesarios tener un router Wi-Fi activo al que conectarse y un dispositivo ethernet que va a hacer de "puente" con el repetidor._
## Procedimiento | Paso a paso
> Según la página web:

| __PASO__ | Línea de código _"Facilitada por el creador del proyecto"_ |
| :----: | :--------------------------------------------------------: |
| _**1.**_ Antes de empezar a instalar y configurar los paquetes, lo primero se debe hacer es una actualización en la Raspberry Pi introduciendo los siguientes dos comandos en el terminal. | ``` sudo apt-get update sudo apt-get upgrade ``` |
| _**2.**_ Hecho esto ya se puede instalar los dos paquetes que se van a utilizar, ejecutando el siguiente comando para instalar **dnsmasq y hostapd.** | ``` sudo apt-get install dnsmasq sudo apt-get install hostapd ``` |
| _**3.**_ Luego, debemos configurar la conexión **wlan0** que se va a usar. Si ya se ha configurado la conexión inalámbrica saltarse hasta el **paso 5.**; de lo contrario, se debe abrir el archivo _wpa-supplicant.conf_ ejecutando el siguiente comando en la Raspberry Pi: | ``` sudo nano /etc/wpa_supplicant/wpa_supplicant.conf ``` |
| _**4.**_ Dentro del archivo añada lo siguiente, asegurándose de sustituir el **ssid** por el nombre de la red a la que quiere conectarse y sustituya el valor **psk** por la contraseña de esa red. Una vez que haya introducido el nombre de la red y la contraseña de la misma, puede guardar el archivo pulsando *CTRL + X* y después pulse *ENTER*. | ``` network={ ssid="networkname" psk="networkpassword" } ``` |
| _**5.**_ Con los paquetes ahora instalados y con la configuración de WiFi hecha, ahora debemos configurar el *dhcpcd* para dar a nuestra Raspberry Pi una dirección IP estática. Para ello modificamos el archivo _dhcpcd.conf_ con el siguiente comando: | ``` sudo nano /etc/dhcpcd.conf ``` |
| _**6.**_ Con los paquetes ahora instalados y con la configuración de WiFi hecha, ahora debemos configurar el *dhcpcd* para dar a nuestra Raspberry Pi una dirección IP estática. Para ello modificamos el archivo _dhcpcd.conf_ con el siguiente comando: | ``` sudo nano /etc/dhcpcd.conf ``` |
| _**7.**_ Con los paquetes ahora instalados y con la configuración de WiFi hecha, ahora debemos configurar el *dhcpcd* para dar a nuestra Raspberry Pi una dirección IP estática. Para ello modificamos el archivo _dhcpcd.conf_ con el siguiente comando: | ``` sudo nano /etc/dhcpcd.conf ``` |
| _**8.**_ Con los paquetes ahora instalados y con la configuración de WiFi hecha, ahora debemos configurar el *dhcpcd* para dar a nuestra Raspberry Pi una dirección IP estática. Para ello modificamos el archivo _dhcpcd.conf_ con el siguiente comando: | ``` sudo nano /etc/dhcpcd.conf ``` |
| _**9.**_ Con los paquetes ahora instalados y con la configuración de WiFi hecha, ahora debemos configurar el *dhcpcd* para dar a nuestra Raspberry Pi una dirección IP estática. Para ello modificamos el archivo _dhcpcd.conf_ con el siguiente comando: | ``` sudo nano /etc/dhcpcd.conf ``` |
| _**10.**_ Con los paquetes ahora instalados y con la configuración de WiFi hecha, ahora debemos configurar el *dhcpcd* para dar a nuestra Raspberry Pi una dirección IP estática. Para ello modificamos el archivo _dhcpcd.conf_ con el siguiente comando: | ``` sudo nano /etc/dhcpcd.conf ``` |
| _**11.**_ Con los paquetes ahora instalados y con la configuración de WiFi hecha, ahora debemos configurar el *dhcpcd* para dar a nuestra Raspberry Pi una dirección IP estática. Para ello modificamos el archivo _dhcpcd.conf_ con el siguiente comando: | ``` sudo nano /etc/dhcpcd.conf ``` |
| _**12.**_ Con los paquetes ahora instalados y con la configuración de WiFi hecha, ahora debemos configurar el *dhcpcd* para dar a nuestra Raspberry Pi una dirección IP estática. Para ello modificamos el archivo _dhcpcd.conf_ con el siguiente comando: | ``` sudo nano /etc/dhcpcd.conf ``` |
| _**13.**_ Con los paquetes ahora instalados y con la configuración de WiFi hecha, ahora debemos configurar el *dhcpcd* para dar a nuestra Raspberry Pi una dirección IP estática. Para ello modificamos el archivo _dhcpcd.conf_ con el siguiente comando: | ``` sudo nano /etc/dhcpcd.conf ``` |
| _**14.**_ Con los paquetes ahora instalados y con la configuración de WiFi hecha, ahora debemos configurar el *dhcpcd* para dar a nuestra Raspberry Pi una dirección IP estática. Para ello modificamos el archivo _dhcpcd.conf_ con el siguiente comando: | ``` sudo nano /etc/dhcpcd.conf ``` |
| _**15.**_ Con los paquetes ahora instalados y con la configuración de WiFi hecha, ahora debemos configurar el *dhcpcd* para dar a nuestra Raspberry Pi una dirección IP estática. Para ello modificamos el archivo _dhcpcd.conf_ con el siguiente comando: | ``` sudo nano /etc/dhcpcd.conf ``` |
| _**16.**_ Con los paquetes ahora instalados y con la configuración de WiFi hecha, ahora debemos configurar el *dhcpcd* para dar a nuestra Raspberry Pi una dirección IP estática. Para ello modificamos el archivo _dhcpcd.conf_ con el siguiente comando: | ``` sudo nano /etc/dhcpcd.conf ``` |
| _**17.**_ Con los paquetes ahora instalados y con la configuración de WiFi hecha, ahora debemos configurar el *dhcpcd* para dar a nuestra Raspberry Pi una dirección IP estática. Para ello modificamos el archivo _dhcpcd.conf_ con el siguiente comando: | ``` sudo nano /etc/dhcpcd.conf ``` |
| _**18.**_ Con los paquetes ahora instalados y con la configuración de WiFi hecha, ahora debemos configurar el *dhcpcd* para dar a nuestra Raspberry Pi una dirección IP estática. Para ello modificamos el archivo _dhcpcd.conf_ con el siguiente comando: | ``` sudo nano /etc/dhcpcd.conf ``` |
| _**19.**_ Con los paquetes ahora instalados y con la configuración de WiFi hecha, ahora debemos configurar el *dhcpcd* para dar a nuestra Raspberry Pi una dirección IP estática. Para ello modificamos el archivo _dhcpcd.conf_ con el siguiente comando: | ``` sudo nano /etc/dhcpcd.conf ``` |
| _**20.**_ Con los paquetes ahora instalados y con la configuración de WiFi hecha, ahora debemos configurar el *dhcpcd* para dar a nuestra Raspberry Pi una dirección IP estática. Para ello modificamos el archivo _dhcpcd.conf_ con el siguiente comando: | ``` sudo nano /etc/dhcpcd.conf ``` |
| _**21.**_ Con los paquetes ahora instalados y con la configuración de WiFi hecha, ahora debemos configurar el *dhcpcd* para dar a nuestra Raspberry Pi una dirección IP estática. Para ello modificamos el archivo _dhcpcd.conf_ con el siguiente comando: | ``` sudo nano /etc/dhcpcd.conf ``` |
| _**22.**_ Con los paquetes ahora instalados y con la configuración de WiFi hecha, ahora debemos configurar el *dhcpcd* para dar a nuestra Raspberry Pi una dirección IP estática. Para ello modificamos el archivo _dhcpcd.conf_ con el siguiente comando: | ``` sudo nano /etc/dhcpcd.conf ``` |
| _**23.**_ Con los paquetes ahora instalados y con la configuración de WiFi hecha, ahora debemos configurar el *dhcpcd* para dar a nuestra Raspberry Pi una dirección IP estática. Para ello modificamos el archivo _dhcpcd.conf_ con el siguiente comando: | ``` sudo nano /etc/dhcpcd.conf ``` |
| _**24.**_ Con los paquetes ahora instalados y con la configuración de WiFi hecha, ahora debemos configurar el *dhcpcd* para dar a nuestra Raspberry Pi una dirección IP estática. Para ello modificamos el archivo _dhcpcd.conf_ con el siguiente comando: | ``` sudo nano /etc/dhcpcd.conf ``` |
| _**25.**_ Con los paquetes ahora instalados y con la configuración de WiFi hecha, ahora debemos configurar el *dhcpcd* para dar a nuestra Raspberry Pi una dirección IP estática. Para ello modificamos el archivo _dhcpcd.conf_ con el siguiente comando: | ``` sudo nano /etc/dhcpcd.conf ``` |

