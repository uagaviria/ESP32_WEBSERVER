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
// Archivo Config.json que deberas subir.
{
  
  "Usuario": "ssid",
  "Contrasena": "password",
  "MqttUsername":"mqttusername",
  "MqttPassword":"mqttpassword",
  "ClientId":"clientid",
  "ConfigPass":"2475"
}  

```

- El programa principal completo se ha subido al repositorio para ser usado libremente.
