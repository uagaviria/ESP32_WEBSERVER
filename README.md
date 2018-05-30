# ESP32_WEBSERVER
El ESP32 hermano mayor del archi reconocido ESP8266, se encuentran en la lista de procesadores diseñados para IoT
mas perseguidos por profecionales y aficionados de la programación y la electrónica.
Una máquina potente que destaca por sus capacidades de comunicación WiFi y Bluetooth.

El ESP32 añade muchas funciones y mejoras respecto al ESP8266, como son mayor potencia, Bluetooth 4.0, encriptación por hadware, sensor de temperatura, sensor hall, sensor táctil, reloj de tiempo real (RTC). más puertos, más buses… ¡más de todo!, Para acabar de redondear y deguastar
de esta poderosa herramienta. Lo que me atrevo a Decir es que el único inconveniente que podemos tener con este gigante es la limitación de conocimiento. Por eso me he dedicado a investigarlo mas a fondo.
Por tal motivo. si alguien desea colaborar con el proyecto o hacerme sujerencias lo puede hacer a mi correo electrónico uagaviria@gmail.com.

## Mas informacion en:
[aprendiendoarduino  https://aprendiendoarduino.wordpress.com/tag/esp32/](https://aprendiendoarduino.wordpress.com/tag/esp32/)



## El programa y la interface:

```cpp
//******************************************************************************************************
// CONFIGURACION DE INTERFACE WEB EN HTML Y BOOTSTRAP.
// Bueno. no sere el mejor programando en html y algunos diran que estoy cometiendo
// muchos errores en este codigo, pero la verdad es que funciona a la perfeccion. 
// fueron varios dias de trabajo, de prueba y error. El resultado lo veran en la imagen de 
// mas abajo. recibo comentarios o mejoras al respecto.
//******************************************************************************************************
const char HTML[] PROGMEM = R"=====(
<!DOCTYPE html>
<html lang="en">
<head>
<title>Bootstrap Example</title>
<meta charset="utf-8">
<meta name="viewport" content="width=device-width, initial-scale=1">
<link rel="stylesheet" href="https://cdnjs.cloudflare.com/ajax/libs/font-awesome/4.7.0/css/font-awesome.min.css">
<script src="https://ajax.googleapis.com/ajax/libs/jquery/3.2.1/jquery.min.js"></script>
<script src="https://maxcdn.bootstrapcdn.com/bootstrap/3.3.7/js/bootstrap.min.js"></script>
</head>
<body>
<form>

<body style="background-color:#F5F6CE;">
</body>

<div class="container well">

  <!--TITULO DE FORMULARIO-->
  <div class="row">
    <div class="col-xs-12">
      <center><h2>APLICACION</h2></center>
    </div>
  </div>


<div class="form-group">
  <label for="confirm" class="cols-sm-10 control-label">Ssid Wifi</label>
  <div class="cols-sm-10">
    <div class="input-group">
    <input type='text' class='form-control' name='usuario' placeholder="Usuario Wifi" size="30" maxlength="128" style="background:#E6E6E6" required autofocus/>
      <span class="input-group-addon"><i class="fa fa-rss-square" style="font-size:36px" aria-hidden="true"  ></i></span>



    </div>
  </div>
</div>

<div class="form-group">
  <label for="confirm" class="cols-sm-2 control-label">Password Wifi</label>
  <div class="cols-sm-10">
    <div class="input-group">
    <input type='text' class='form-control' name='contrasena' placeholder="Password Wifi" size="30" maxlength="128" style="background:#E6E6E6" required autofocus/>
      <span class="input-group-addon"><i class="fa fa-cogs" style="font-size:36px"></i></span>

    </div>
  </div>
</div>

<div class="form-group">
  <label for="confirm" class="cols-sm-2 control-label">MQTT Username</label>
  <div class="cols-sm-10">
    <div class="input-group">
    <input type='text' class='form-control' name='username' placeholder="Username Cayenne"  size="30" maxlength="128" style="background:#E6E6E6" required autofocus/>
      <span class="input-group-addon"><i class="fa fa-id-card-o" style="font-size:36px"></i></span>

    </div>
  </div>
</div>

<div class="form-group">
  <label for="confirm" class="cols-sm-2 control-label">MQTT Password</label>
  <div class="cols-sm-10">
    <div class="input-group">
    <input type='text' class='form-control' name='password' placeholder="Password Cayenne" size="30" maxlength="128" style="background:#E6E6E6" required autofocus/>
      <span class="input-group-addon"><i class="fa fa-lock fa-lg" style="font-size:36px"></i></span>

    </div>
  </div>
</div>

<div class="form-group">
  <label for="confirm" class="cols-sm-2 control-label">client ID</label>
  <div class="cols-sm-10">
    <div class="input-group">
    <input type='text' class='form-control' name='id' placeholder="clientID Cayenne" size="30" maxlength="128" style="background:#E6E6E6" required autofocus/>
      <span class="input-group-addon"><i class="fa fa-podcast" style="font-size:36px"></i></span>

    </div>
  </div>
</div>

<div class="form-group">
  <label for="confirm" class="cols-sm-2 control-label">Config Code</label>
  <div class="cols-sm-10">
    <div class="input-group">
    <input type='text' class='form-control' name='config' placeholder="Config Code" size="30" maxlength="128" style="background:#E6E6E6" required autofocus/>
      <span class="input-group-addon"><i class="fa fa-shield" style="font-size:36px"></i></span>

    </div>
  </div>
</div>
<Br>

<input type='submit' value='Enviar' style="width:150px; height:35px>

</form>"

</body>
</html>
)=====";        

```

![Aplicacion web Hecha en bootstrap y guardada en progme, del esp32](https://github.com/uagaviria/ESP32_WEBSERVER/blob/master/imagenes/app.jpg) 
![WifiManagerAsync ](https://github.com/uagaviria/ESP32_WEBSERVER/blob/master/imagenes/wifimanager.png)

### Arduinojson y SPIFFS.
- Desafortunadamente desde Atom no esta implementado subir archivos a la flash del ESP32, solo al  ESP8266. Pero desde el entorno de arduino si añadiendo ciertos archivos.
una imagen vale mas que mil palabras. Allí vas a poner los archivos .jar que te voy a dar para que puedas subir lo que desees a la flash.
una vez esten alli vas al entorno de arduino y veras dos nuevas lineas en herramientas. lo veras en la imagen a continuación.
el ESP32FS y el ESP8266FS.
[Link de descarga ](https://github.com/uagaviria/ESP32_WEBSERVER/tree/master/SPIFFS_UPLOAD)


![Subir archivos a la flash](https://raw.githubusercontent.com/uagaviria/ESP32_WEBSERVER/master/imagenes/spiffs.png)

Una vez cumpliendo con estos requerimientos debemos subir el archivo config.json que se encuentra dentro del proyecto en la carpeta data.

### Cómo usar SPIFFS para ESP32 en el IDE Arduino:
Sencillamente se ha de crear una carpeta llamada "data" en la carpeta del Sketch y pulsar el menú "Herramientas" --> "ESP32 Sketch Data Upload". En la barra de estado veremos el progreso de la operación.
Advertencia: ¡Esta operación borra todo el contenido y sube lo que haya en la carpeta data, no conserva los otros archivos si los tiene allí!

```cpp
#if defined(ESP8266)
#include <ESP8266WiFi.h>          
#else
#include <WiFi.h>          
#endif

//needed for library
#include <DNSServer.h>
#if defined(ESP8266)
#include <ESP8266WebServer.h>
#else
#include <WebServer.h>
#endif
#include <WiFiManager.h>         

```

- Initialize library, in your setup function add
```cpp
WiFiManager wifiManager;
```

- Also in the setup function add
```cpp
//first parameter is name of access point, second is the password
wifiManager.autoConnect("AP-NAME", "AP-PASSWORD");
```
if you just want an unsecured access point
```cpp
wifiManager.autoConnect("AP-NAME");
```
or if you want to use and auto generated name from 'ESP' and the esp's Chip ID use
```cpp
wifiManager.autoConnect();
```

After you write your sketch and start the ESP, it will try to connect to WiFi. If it fails it starts in Access Point mode.
While in AP mode, connect to it then open a browser to the gateway IP, default 192.168.4.1, configure wifi, save and it should reboot and connect.

Also see [examples](https://github.com/tzapu/WiFiManager/tree/master/examples).

## Documentation

#### Password protect the configuration Access Point
You can and should password protect the configuration access point.  Simply add the password as a second parameter to `autoConnect`.
A short password seems to have unpredictable results so use one that's around 8 characters or more in length.
The guidelines are that a wifi password must consist of 8 to 63 ASCII-encoded characters in the range of 32 to 126 (decimal)
```cpp
wifiManager.autoConnect("AutoConnectAP", "password")
```

#### Callbacks
##### Enter Config mode
Use this if you need to do something when your device enters configuration mode on failed WiFi connection attempt.
Before `autoConnect()`
```cpp
wifiManager.setAPCallback(configModeCallback);
```
`configModeCallback` declaration and example
```cpp
void configModeCallback (WiFiManager *myWiFiManager) {
  Serial.println("Entered config mode");
  Serial.println(WiFi.softAPIP());

  Serial.println(myWiFiManager->getConfigPortalSSID());
}
```

##### Save settings
This gets called when custom parameters have been set **AND** a connection has been established. Use it to set a flag, so when all the configuration finishes, you can save the extra parameters somewhere.

See [AutoConnectWithFSParameters Example](https://github.com/tzapu/WiFiManager/tree/master/examples/AutoConnectWithFSParameters).
```cpp
wifiManager.setSaveConfigCallback(saveConfigCallback);
```
`saveConfigCallback` declaration and example
```cpp
//flag for saving data
bool shouldSaveConfig = false;

//callback notifying us of the need to save config
void saveConfigCallback () {
  Serial.println("Should save config");
  shouldSaveConfig = true;
}
```

#### Configuration Portal Timeout
If you need to set a timeout so the ESP doesn't hang waiting to be configured, for instance after a power failure, you can add
```cpp
wifiManager.setConfigPortalTimeout(180);
```
which will wait 3 minutes (180 seconds). When the time passes, the autoConnect function will return, no matter the outcome.
Check for connection and if it's still not established do whatever is needed (on some modules I restart them to retry, on others I enter deep sleep)

#### On Demand Configuration Portal
If you would rather start the configuration portal on demand rather than automatically on a failed connection attempt, then this is for you.

Instead of calling `autoConnect()` which does all the connecting and failover configuration portal setup for you, you need to use `startConfigPortal()`. __Do not use BOTH.__

Example usage
```cpp
void loop() {
  // is configuration portal requested?
  if ( digitalRead(TRIGGER_PIN) == LOW ) {
    WiFiManager wifiManager;
    wifiManager.startConfigPortal("OnDemandAP");
    Serial.println("connected...yeey :)");
  }
}
```
See example for a more complex version. [OnDemandConfigPortal](https://github.com/tzapu/WiFiManager/tree/master/examples/OnDemandConfigPortal)

#### Custom Parameters
You can use WiFiManager to collect more parameters than just SSID and password.
This could be helpful for configuring stuff like MQTT host and port, [blynk](http://www.blynk.cc) or [emoncms](http://emoncms.org) tokens, just to name a few.
**You are responsible for saving and loading these custom values.** The library just collects and displays the data for you as a convenience.
Usage scenario would be:
- load values from somewhere (EEPROM/FS) or generate some defaults
- add the custom parameters to WiFiManager using
 ```cpp
 // id/name, placeholder/prompt, default, length
 WiFiManagerParameter custom_mqtt_server("server", "mqtt server", mqtt_server, 40);
 wifiManager.addParameter(&custom_mqtt_server);

 ```
- if connection to AP fails, configuration portal starts and you can set /change the values (or use on demand configuration portal)
- once configuration is done and connection is established [save config callback]() is called
- once WiFiManager returns control to your application, read and save the new values using the `WiFiManagerParameter` object.
 ```cpp
 mqtt_server = custom_mqtt_server.getValue();
 ```  
This feature is a lot more involved than all the others, so here are some examples to fully show how it is done.
You should also take a look at adding custom HTML to your form.

- Save and load custom parameters to file system in json form [AutoConnectWithFSParameters](https://github.com/tzapu/WiFiManager/tree/master/examples/AutoConnectWithFSParameters)
- *Save and load custom parameters to EEPROM* (not done yet)

#### Custom IP Configuration
You can set a custom IP for both AP (access point, config mode) and STA (station mode, client mode, normal project state)

##### Custom Access Point IP Configuration
This will set your captive portal to a specific IP should you need/want such a feature. Add the following snippet before `autoConnect()`
```cpp
//set custom ip for portal
wifiManager.setAPStaticIPConfig(IPAddress(10,0,1,1), IPAddress(10,0,1,1), IPAddress(255,255,255,0));
```

##### Custom Station (client) Static IP Configuration
This will make use the specified IP configuration instead of using DHCP in station mode.
```cpp
wifiManager.setSTAStaticIPConfig(IPAddress(192,168,0,99), IPAddress(192,168,0,1), IPAddress(255,255,255,0));
```
There are a couple of examples in the examples folder that show you how to set a static IP and even how to configure it through the web configuration portal.

#### Custom HTML, CSS, Javascript
There are various ways in which you can inject custom HTML, CSS or Javascript into the configuration portal.
The options are:
- inject custom head element
You can use this to any html bit to the head of the configuration portal. If you add a `<style>` element, bare in mind it overwrites the included css, not replaces.
```cpp
wifiManager.setCustomHeadElement("<style>html{filter: invert(100%); -webkit-filter: invert(100%);}</style>");
```
- inject a custom bit of html in the configuration form
```cpp
WiFiManagerParameter custom_text("<p>This is just a text paragraph</p>");
wifiManager.addParameter(&custom_text);
```
- inject a custom bit of html in a configuration form element
Just add the bit you want added as the last parameter to the custom parameter constructor.
```cpp
WiFiManagerParameter custom_mqtt_server("server", "mqtt server", "iot.eclipse", 40, " readonly");
```

#### Filter Networks
You can filter networks based on signal quality and show/hide duplicate networks.

- If you would like to filter low signal quality networks you can tell WiFiManager to not show networks below an arbitrary quality %;
```cpp
wifiManager.setMinimumSignalQuality(10);
```
will not show networks under 10% signal quality. If you omit the parameter it defaults to 8%;

- You can also remove or show duplicate networks (default is remove).
Use this function to show (or hide) all networks.
```cpp
wifiManager.setRemoveDuplicateAPs(false);
```

#### Debug
Debug is enabled by default on Serial. To disable add before autoConnect
```cpp
wifiManager.setDebugOutput(false);
```


### Contributions and thanks
The support and help I got from the community has been nothing short of phenomenal. I can't thank you guys enough. This is my first real attept in developing open source stuff and I must say, now I understand why people are so dedicated to it, it is because of all the wonderful people involved.

__THANK YOU__

[Shawn A](https://github.com/tablatronix)

[Maximiliano Duarte](https://github.com/domonetic)

[alltheblinkythings](https://github.com/alltheblinkythings)

[Niklas Wall](https://github.com/niklaswall)

[Jakub Piasecki](https://github.com/zaporylie)

[Peter Allan](https://github.com/alwynallan)

[John Little](https://github.com/j0hnlittle)

[markaswift](https://github.com/markaswift)

[franklinvv](https://github.com/franklinvv)

[Alberto Ricci Bitti](https://github.com/riccibitti)

[SebiPanther](https://github.com/SebiPanther)

[jonathanendersby](https://github.com/jonathanendersby)

[walthercarsten](https://github.com/walthercarsten)

Sorry if i have missed anyone.

#### Inspiration
- http://www.esp8266.com/viewtopic.php?f=29&t=2520
