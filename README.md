# RFID_ESP32
## PN532 y ESP32
Para utilizar el lector RFID PN532 con ESP32 es necesario modificar la librería ya que la librería original de Adafruit no es 100% compatible con un ESP32.

Para esto podemos modificar la librería directamente o podemos utilizar la librería UNIT_PN532 que ya viene modificada y solamente hay que descargarla y agregarla a nuestro IDE.

## Modificación a la librería
Para usar el lector PN532 con ESP32 hay que modificar la librería, ya que la tasa de bits que viene predefinida en la librería de Adafruit es demasiado rápida para el ESP32 por lo cual se debe modificar este dato para poder utilizarlo con esta placa.

El problema que genera no modificar la tasa de bits, es la desconexión constante de la placa, el no reconocimiento de la placa PN532, la no lectura de las tarjetas RFID o que el programa entre en un bucle y se tenga que estar reiniciando constantemente la placa.

##Solución
Hay dos soluciones para este problema, la primera es descargar la librería que se muestra a continuación, esta librería ya esta modificada para ser usada con el ESP32 y que no genere ningún error.

[Librería UNIT_PN532](https://blog.uelectronics.com/wp-content/uploads/2021/10/UNIT-PN532.zip)

La segunda opción es modificar la siguiente parte de código dentro de la librería original de Adafruit.


Tenemos que modificar el dato que esta en el recuadro por el siguiente valor: “100000”, esto nos dará una mejor comunicación con el ESP32 y así tendremos una conexión mas estable entre el PN532 y el ESP32. Esto sirve para la comunicación del PN532 por SPI, se recomienda usar SPI ya que es mas estable y la librería esta mejor diseñada para ese tipo de comunicación.

## Conexión ESP32 y PN532

Estas son las conexiones que se tienen que hacer entre el lector PN532 y el ESP32, la comunicación que estaremos manejando será por SPI, revisa que tengas configurado el PN532 para este tipo de comunicación.

guia obtenida de https://blog.uelectronics.com/tarjetas-desarrollo/lee-tarjetas-rfid-con-pn532-y-esp32/ 
