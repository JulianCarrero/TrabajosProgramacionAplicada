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
Para configurar el repetidor WIFI con nuestra tarjeta Raspberry Pi Wifi Extender se recomienda (como lo indica en la página web el desarrollador) usar el paquete _dnsmasq_; ya que actúa como nuestro servidor DNS y DHCP para nuestras conexiones. También necesitaremos utilizar el paquete hostapd, este es el paquete que nos permitirá configurar uno de nuestros módulos Wi-Fi como punto de acceso o raíz.

**ACLARACIÓN**: _Recordar que para este proyecto es necesarios tener un router Wi-Fi activo al que conectarse y un dispositivo ethernet que va a hacer de "puente" con el repetidor._
## Procedimiento | Paso a paso

