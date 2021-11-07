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

| __PASO__ | Línea de código _"Facilitada por el creador del proyecto"_ |
| :----: | :--------------------------------------------------------: |
| _**6.**_ Dentro de este archivo toca añadir las siguientes líneas al final, esto configurará la conexión **wlan1**. Ahora se guardan y se sale del archivo presionando _CTRL + X_ y luego presionando _ENTER._ | ``` interface wlan1 static ip_address=192.168.220.1/24 static routers=192.168.220.0 ``` |
| _**7.**_ Ahora se hace necesario reiniciar el servicio __dhcpd__ para que cargue todos los cambios de configuración. | ``` sudo service dhcpcd restart ``` |
| _**8.**_ A continuación, toca ajustar nuestra configuración _hostapd_, para ello empezamos a editar el archivo de configuración ejecutando el siguiente comando en el Raspberry Pi. | ``` sudo nano /etc/hostapd/hostapd.conf ``` |
| _**9.**_ En este archivo ahora se debe escribir las siguientes líneas, estas básicamente configuran la interacción con el dispositivo __wlan__. | ![Línea de código #9](https://scontent.fbog2-5.fna.fbcdn.net/v/t39.30808-6/251611112_1275384239607451_8673831666808873981_n.jpg?_nc_cat=103&_nc_rgb565=1&ccb=1-5&_nc_sid=0debeb&_nc_ohc=GBQ1srpimpAAX89PLR0&_nc_ht=scontent.fbog2-5.fna&oh=b09fa2c364d2ccac9294c99136cde43b&oe=618C8D74) |
| _**10.**_ Una vez hecho esto, se debe modificar los archivos _hostapd_ en __/etc/default/ y /etc/init.d/.__ Estos archivos son los que hostapd leerá para encontrar el nuevo archivo de configuración que se creó en los pasos anteriores. | ``` sudo nano /etc/default/hostapd ``` |

| __PASO__ | Línea de código _"Facilitada por el creador del proyecto"_ |
| :----: | :--------------------------------------------------------: |
| _**11.**_ En este archivo, es necesario encontrar esta siguiente línea y reemplazarla. | ![Línea de código #11](https://scontent.fbog2-3.fna.fbcdn.net/v/t39.30808-6/254518631_1275381869607688_468648728733350244_n.jpg?_nc_cat=106&_nc_rgb565=1&ccb=1-5&_nc_sid=0debeb&_nc_ohc=H1uWIuA1B0QAX-A7v1X&_nc_ht=scontent.fbog2-3.fna&oh=57b74623f500e135f16bf94929053dae&oe=618D0D19) |
| _**12.**_ Ahora se edita el segundo archivo de configuración, este archivo se encuentra dentro de la carpeta __init.d.__ Es posible editar el archivo con el siguiente comando: | ``` sudo nano /etc/init.d/hostapd ``` |
| _**13.**_ En este archivo, se hace recomendable encontrar la siguiente línea y reemplazarla. | ![Línea de código #13](https://scontent.fbog2-4.fna.fbcdn.net/v/t39.30808-6/252769433_1275382726274269_3194382047253154982_n.jpg?_nc_cat=101&_nc_rgb565=1&ccb=1-5&_nc_sid=0debeb&_nc_ohc=iiD7VI1n4NkAX9RIWoX&tn=ojhnKD1H4nuW7Cr9&_nc_ht=scontent.fbog2-4.fna&oh=07780ad1b1acdce91646992e43b1f216&oe=618B904D) |
| _**14.**_ Con _hostapd_ ahora configurado se pasa a configurar __dnsmasq,__ antes de empezar a editar su configuración se moverá la que viene por defecto a una nueva ubicación. Esto se hace con el siguiente comando: | ``` sudo mv /etc/dnsmasq.conf /etc/dnsmasq.conf.orig ``` |
| _**15.**_ Ahora que el archivo de configuración original ha sido movido se empieza a crear el propio archivo de configuración. | ``` sudo nano /etc/dnsmasq.conf ``` |

| __PASO__ | Línea de código _"Facilitada por el creador del proyecto"_ |
| :----: | :--------------------------------------------------------: |
| _**16.**_ A este archivo ahora se agrega las siguientes líneas, estas líneas básicamente le dicen al servicio __dnsmasq__ como manejar todas las conexiones que lleguen. | ![Línea de código #16](https://scontent.fbog2-4.fna.fbcdn.net/v/t39.30808-6/252011987_1275388996273642_407121190281124964_n.jpg?_nc_cat=111&_nc_rgb565=1&ccb=1-5&_nc_sid=0debeb&_nc_ohc=U2A_yXXXd1QAX9FmlsO&_nc_oc=AQntMvfaTxRvcHFwh03Qxyo1nDAyuQVPv-JFEWG1rkBg5r7RYo9weP-7T99KZM4DRNdPvx9liJa3OBE13erBrKAz&_nc_ht=scontent.fbog2-4.fna&oh=5df8a21ec811c595f62368f538dea663&oe=618C91A3) |
| _**17.**_ A continuación, se debe configurar el Raspberry Pi para que reenvíe todo el tráfico de la conexión _wlan1_ a la conexión _wlan0._ Primero esto se habilita a través del archivo de configuración **sysctl.conf.** | ``` sudo nano /etc/sysctl.conf ``` |
| _**18.**_ Dentro de este archivo hay que buscar la siguiente línea, y eliminar el hashtag (#) del principio de la misma. | ![Línea de código #18](https://scontent.fbog2-5.fna.fbcdn.net/v/t39.30808-6/252891564_1275384819607393_2218546226550332972_n.jpg?_nc_cat=110&_nc_rgb565=1&ccb=1-5&_nc_sid=0debeb&_nc_ohc=pKnh3zGf4ZoAX_FCiFj&_nc_ht=scontent.fbog2-5.fna&oh=9ca71e8d1401b8ab3aa053a246f05300&oe=618BCF89) |
| _**19.**_ Ahora se puede ejecutar el siguiente comando para activarlo: | ``` sudo sh -c "echo 1 > /proc/sys/net/ipv4/ip_forward" ``` |
| _**20.**_ Con el Forwarding __IPv4__ ahora activo se configura un _NAT_ entre la interfaz __wlan0__ y la interfaz **wlan1.** Básicamente, esto reenviará todo el tráfico del punto de acceso a la conexión ethernet. | ``` sudo iptables -t nat -A POSTROUTING -o wlan0 -j MASQUERADE sudo iptables -A FORWARD -i wlan0 -o wlan1 -m state --state RELATED,ESTABLISHED -j ACCEPT sudo iptables -A FORWARD -i wlan1 -o wlan0 -j ACCEPT ``` |

| __PASO__ | Línea de código _"Facilitada por el creador del proyecto"_ |
| :----: | :--------------------------------------------------------: |
| _**21.**_ Por supuesto, el archivo se vacía en cada arranque de la Raspberry Pi por lo que será necesario guardar las "reglas" en algún lugar para que se carguen de nuevo en cada arranque. | ``` sudo sh -c "iptables-save > /etc/iptables.ipv4.nat" ``` |
| _**22.**_ Ahora, con estas "reglas" guardadas de forma segura, es necesario hacer que este archivo se cargue de nuevo en cada reinicio. La manera más simple de manejar esto es modificar el archivo _rc.local._ | ``` sudo nano /etc/rc.local ``` |
| _**23.**_ Ahora que se esta en este archivo, se debe añadir la línea de abajo. Asegúrese de que esta línea aparece por encima de la _salida 0._ Esta línea básicamente lee la configuración del archivo **iptables.ipv4.nat** y la carga en el _iptables._ | ![Línea de código #23](https://scontent.fbog2-4.fna.fbcdn.net/v/t39.30808-6/252133503_1275385496273992_5074239873772475602_n.jpg?_nc_cat=107&_nc_rgb565=1&ccb=1-5&_nc_sid=0debeb&_nc_ohc=Q0k-ScYME10AX-cAL6r&_nc_ht=scontent.fbog2-4.fna&oh=ec9684c4dccb176401b59931d92e3be1&oe=618BBE82) |
| _**24.**_ Finalmente todo lo que se debe hacer ahora es iniciar los dos servicios y habilitarlos en _systemctl._ | ![Línea de código #24](https://scontent.fbog2-5.fna.fbcdn.net/v/t39.30808-6/252236248_1275386009607274_1259079955733444516_n.jpg?_nc_cat=110&_nc_rgb565=1&ccb=1-5&_nc_sid=0debeb&_nc_ohc=591SSirWK90AX9Pw-ZY&_nc_ht=scontent.fbog2-5.fna&oh=c440755735178d3d6f5e103ead0e0d61&oe=618D09A3) |
| _**25.**_ Ahora se tiene un punto de acceso inalámbrico Raspberry Pi totalmente operativo, para asegurarse de que funciona: Se recomienda utilizar cualquier dispositivo inalámbrico y conéctelo a el nuevo punto de acceso utilizando el _SSID y la frase de contraseña WPA_ que se estableció anteriormente. | ``` sudo reboot ``` |

> Para asegurarse de que todo funcione correctamente, es mejor intentar reiniciar ahora. Esto asegurará que todo se vuelva a habilitar con éxito cuando la Raspberry Pi se inicie de nuevo. Ejecute el siguiente comando para reiniciar la Raspberry Pi:

## Limitaciones del proyecto
- [x] Una de las limitaciones del proyecto tiene que ver con el **dongle wifi** dado que: La mayoría de estos componentes cuentan con velocidad limitadas en redes de _2.4GHz_ (la más comunes), por lo cual, personas que tengan instalados paquetes con altas tasas de velocidad __(superiores a 150Mbps como lo indican algunos fabricadores)__ pueden verse afectadas al no aprovechar todo la velocidad de su WIFI, por lo tanto se pierde velocidad pero se gana estabilidad en la señal; una de las formas de solucionar este problema es cambiar la banda de red por una mucho mayor o en su defecto invertir más en el dongle wifi.
- [x] **Compatibilidad con el software:** Dado los diferentes sistemas operativos existentes es posible que como pasa con otros muchos otros repetidores se presenten problemas con algunos _dispositivos,_ por lo que, este proyecto no es algo **universal** y puede presentar fallas para aparatos particulares.
- [x] **La fuerza de la señal amplificada no puede ser la esperada:** Si el repetidor construido no es compatible con el _hardware actual_ de la red inalámbrica no se podrá aprovechar al 100% su capacidad.
  * __Seguridad:__ Al momento de enlazar el dispositivo al router es altamente probable que la _seguridad_ se expongan en mayor medida, limitando no solo la _privacidad_ sino también la exposición a que terceros se conecten a nuestra conexión a Internet.
  * Al no contar con una __antena propia__ la cobertura o areá que puede cubrir el repetidor es mucho menor y con obstáculos (paredes, puertes, etc) la _interferencia_ puede estar presente.
    - La cantidad de veces que debe **reiniciarse** para poder tener un funcionamiento óptimo y la __peridiocidad__ con la que debe hacerse genera perdidas de conexión muy a menudo.

## Referencias
- [x] [25 proyectos con Raspberry Pi que explotan todo su potencial](https://www.ionos.es/digitalguide/servidores/know-how/un-vistazo-a-proyectos-basados-en-raspberry-pi/)
- [x] [Simple Raspberry Pi WiFi Extender](https://pimylifeup.com/raspberry-pi-wifi-extender/)

## Anexos
> Tener en cuenta la siguiente terminología para un desarrollo óptimo del proyecto
- [Hostapd](https://wiki.gentoo.org/wiki/Hostapd) 
  - [El DHCP y la configuración de redes](https://www.ionos.es/digitalguide/servidores/configuracion/que-es-el-dhcp-y-como-funciona/)
    - [What is DNS? | How DNS works](https://www.cloudflare.com/es-es/learning/dns/what-is-dns/)
      - [dnsmasq (Español)](https://wiki.archlinux.org/title/Dnsmasq_(Español))

