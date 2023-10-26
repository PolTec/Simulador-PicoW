# Unidad 3: Modularizacion
 
# Tabla de Contenido
3.1 Simulador PicoW

Descripcion

Codigo en C para programar "Hola Mundo"

Evaluacion

Recursos

# 3.1 Simulador PicoW

## Descripcion
A traves de este trabajo de la Unidad 3 no estamos adentrando a lo que es a la Modularizacion, es decir, que estamos conociendo 2 areas que son lo que es la Programacion y lo que es la Electronica a traves de diferentes herramientas que se nos muestran, en el cual, una de ellas un simulador en la plataforma de Wokwi y tambien el programa de Arduino IDE.

En esta primera actividad, estaremos experimentando lo que la Simulacion de una tarjet Raspberry Pi Pico W, a traves de la herramienta Wowki, ya que esta nos proporciona un entorno virtual en el que podemos diseñar, construir y probar circuitos electrónicos en tiempo real. Esto nos permite experimentar con conceptos de electrónica sin necesidad de hardware físico, lo que es especialmente útil para principiantes.

Para esto, utilizaremos esta simulador para programar un "Hola Mundo"

## Codigo en C para programar "Hola Mundo"

```C
/*
 * Nombre del Archivo: main.c
 * Autor:   [Lopez Rangel Kevin Paul]
 * Correo:  [l21210392@tectijuana.edu.mx]
 * Fecha:   [24/10/2023]
 * Curso:   Lenguajes de Interfaz, TECNM Campus ITT
 * 
 * Objetivo:
 * Este programa está diseñado para [programar el Hola Mundo a traves del Simulador Pico W].
 *
 * Historial de Revisiones:
 * [24/10/2023]        [Lopez Rangel Kevin Paul] - Creado
 * [25/10/2023]        [Lopez Rangel Kevin Paul] - Actualizado para añadir [correccion de codigo para la ejecucion de Raspberry Pi Pico W]
 * 
 */

#include <stdio.h>
#include "pico/stdlib.h"
#include "pico/cyw43_arch.h"
#include "hardware/gpio.h"

const uint ledPin = 25; // Pin GPIO al que está conectado el LED

int main() {
    stdio_init_all();
    
    // Inicializa la librería Pico Standard Library
    stdio_init_all();

    // Inicializa el sistema de GPIO
    gpio_init(ledPin);

    // Configura el pin del LED como una salida
    gpio_set_dir(ledPin, GPIO_OUT);

    while (1) {
        // Enciende el LED
        gpio_put(ledPin, 1);
        sleep_ms(1000); // Espera 1 segundo

        // Apaga el LED
        gpio_put(ledPin, 0);
        sleep_ms(1000); // Espera 1 segundo
    }
    return 0;
}

// Visualizacion del Programa en Hardware

  "version": 1,
  "author": "LOPEZ RANGEL KEVIN PAUL",
  "editor": "wokwi",
  "parts": [
    {
      "type": "board-pi-pico-w",
      "id": "pico",
      "top": -51.25,
      "left": -121.25,
      "attrs": { "builder": "pico-sdk" }
    },
    {
      "type": "wokwi-lcd1602",
      "id": "lcd1",
      "top": -51.2,
      "left": 34.4,
      "attrs": { "pins": "i2c" }
    },
    { "type": "wokwi-led", "id": "led1", "top": -90, "left": -197.8, "attrs": { "color": "red" } }
  ],
  "connections": [
    [ "pico:GP0", "$serialMonitor:RX", "", [] ],
    [ "pico:GP1", "$serialMonitor:TX", "", [] ],
    [ "pico:GP0", "lcd1:SDA", "violet", [ "h115.2", "v67.2" ] ],
    [ "pico:GP1", "lcd1:SCL", "blue", [ "h0" ] ],
    [ "pico:VBUS", "lcd1:VCC", "red", [ "h0" ] ],
    [ "pico:GND.8", "lcd1:GND", "black", [ "h0" ] ],
    [ "led1:A", "pico:GP1", "green", [ "v0" ] ],
    [ "led1:C", "pico:GND.1", "black", [ "v0" ] ]
  ],
  "dependencies": {}
}

//Visualizacion para la ejecucion de los modulos para el "Hola Mundo"
# modulos
from machine import Pin, I2C
from time import sleep

from pico_i2c_lcd import I2cLcd

i2c=I2C(0,sda=Pin(0), scl=Pin(1), freq=400000)

I2C_ADDR=i2c.scan()[0]

#crear objeto tipo lcd
lcd=I2cLcd(i2c,I2C_ADDR,2,16)

#LOOP
while True:
    lcd.putstr("Hola mundo")
    sleep(250)
    lcd.clear()
    sleep(1)
```

## Evalucion
100% DEPOSTAR EL URL de su Wokwi funcionando Incluir el templete del código sin el no se recibirán las practicas.

## Recursos
Link del Wokwi: https://wokwi.com/projects/379538589342889985


# 3.3 Simulador PicoW (Wokwi y Arduino IDE)

## Descripcion
A traves de esta actividad, nos ponen varios puntos de elaboracion para comprender un poco mejor cada actividad en las herramientas que nos presentaron para experimentar lo que es trabajar de manera mas practica y eficiente.
Lo que debiamos de hacer en este punto, debiamos primero ejecutar nuevamente un "Hola Mundo" en Wokwi, seguido de eso con un libro de ejercicios que nos proporciona el profesor deberiamos de escoger un ejercicio de un nivel basico e implementarlo tambien en Wokwi.
Seguido de esto, nos dirigimos a la herramienta de Arduino IDE en el cual debiamos de correr un ejemplo que se nos muestra a traves del ASCIITABLE y ya por ultimo con el ejercicio que escogimos, ejecutarlo en el mismo segmento

## Reflexion
A decir verdad, fue un reto en cada herramienta que se nos muestra, ya que nos muestra la importancia de como se trabaja en ambas areas que se nos muestran, tanto en la Programacion para implementar los codigos que deseamos ejecutar al igual que en la Electronica, ya que nos muestran en como trabjar en una herramienta fisica y sobre como podemos almacenar nuestros programas en dicho momento.

En la plataforma Wokwi no tuve problema de como elaborarlo, pero de igual manera no quiere decir que es facil, tienes que saber como utilizarlo mediante la herramienta fisica con la que deseas trabajar y sobre que otras cosas, le quieres proporcionar ya sea librerias para los codigos, asi como componentes fisicos para elaborar de una manera mas profesional.

Ahora, trabajando con Arduino IDE, a decir verdad fue algo para mi algo complicado sobre como implementar los codigos en este tipo de herramientas, en si se podria decir que es algo mucho mas extenso, ya que nos muestra un mundo mas abierto sobre como se debe de elaborar pero ahora en ves de ser un simulador, es trabajar ya con los componentes fisicos que deseas trabajar y sobre en que lenguaje de programacion deseas implementarlo, pero de hacerlo de una manera mas cuidadosa.

A continuacion mostrare los codigos que se utilizaron:

# Codigos
## "Hola Mundo" en la Herramienta Wokwi

```C
/*
 * Nombre del Archivo: main.c
 * Autor:   [Lopez Rangel Kevin Paul]
 * Correo:  [l21210392@tectijuana.edu.mx]
 * Fecha:   [24/10/2023]
 * Curso:   Lenguajes de Interfaz, TECNM Campus ITT
 * 
 * Objetivo:
 * Este programa está diseñado para [programar el Hola Mundo a traves del Simulador PicoW].
 *
 * Historial de Revisiones:
 * [24/10/2023]        [Lopez Rangel Kevin Paul] - Creado
 * [24/20/2023]        [Lopez Rangel Kevin Paul] - Actualizado para añadir [correccion de codigo para la ejecucion de Raspberry Pi Pico W]
 *
 */
#include <stdio.h>
#include "pico/stdlib.h"
#include "pico/cyw43_arch.h"

int main() {
  stdio_init_all();
  while (true) {
    printf("Hola, Mundo!\n");
    sleep_ms(250);
  }
}

//Visualizacion de la Programacion del Hardware
{
  "version": 1,
  "author": "LOPEZ RANGEL KEVIN PAUL",
  "editor": "wokwi",
  "parts": [
    {
      "type": "board-pi-pico-w",
      "id": "pico",
      "top": 0,
      "left": 0,
      "attrs": { "builder": "pico-sdk" }
    }
  ],
  "connections": [ [ "pico:GP0", "$serialMonitor:RX", "", [] ], [ "pico:GP1", "$serialMonitor:TX", "", [] ] ],
  "dependencies": {}
}
```

## Ejercicio de ver 25 numeros Enteros y verificar si es "Impar" o "Par" en Wokwi

```C
/*
Nombre del Archivo: Par o Impar
Autor: Lopez Rangel Kevin Paul 21210392
Correo: l21210392@tectijuana.edu.mx
Fecha: 25/10/2023
Curso: Lenguaje de Interfaz, TECNM CAMPUS ITT

Objetivo:
Escribir un programa que acepte 25 enteros positivos como datos y describir cada uno como "impar" o "par"

Historial de Revisiones
25/10/2023          Lopez Rangel Kevin Paul
*/

#include "pico/stdlib.h"   // Incluye la biblioteca "pico/stdlib.h" para utilizar las funciones de la Raspberry Pi Pico.
#include <stdio.h>         // Incluye la biblioteca estándar de entrada/salida para funciones como printf.

/**
 * Determina si un número entero dado es par o impar.
 *
 * @param num: Un número entero.
 * @return: 1 si el número es par, 0 si el número es impar.
 */
int esPar(int num) {
    if (num % 2 == 0) {
        return 1;  // El número es par.
    } else {
        return 0;  // El número es impar.
    }
}

/**
 * Acepta 25 números enteros positivos como entrada y describe cada uno como par o impar.
 */
void describirEnteros() {
    int num;
    printf("Ingresa 25 números enteros positivos:\n");

    for (int i = 1; i <= 25; i++) {
        scanf("%d", &num);

        if (num < 0) {
            printf("Entrada no válida: El número debe ser positivo.\n");
            i--;  // Decrementando i para repetir la iteración actual.
            continue;
        }

        if (esPar(num)) {
            printf("%d es par.\n", num);
        } else {
            printf("%d es impar.\n", num);
        }
    }
}

int main() {
    stdio_init_all();  // Inicializa las funciones de entrada/salida estándar.

    describirEnteros();
    return 0;
}

//Visualizacion del Ejercicio en hardware
{
  "version": 1,
  "author": "LOPEZ RANGEL KEVIN PAUL",
  "editor": "wokwi",
  "parts": [
    {
      "type": "wokwi-pi-pico",
      "id": "pico",
      "top": 0,
      "left": 0,
      "attrs": { "builder": "pico-sdk" }
    }
  ],
  "connections": [ [ "pico:GP0", "$serialMonitor:RX", "", [] ], [ "pico:GP1", "$serialMonitor:TX", "", [] ] ],
  "dependencies": {}
}
```

## Ejemplo en ASCII-Table de la Raspberry Pi Pico W en Arduino IDE

```C
/*
 * Nombre del Archivo: Ascii Table
 * Autor:   Lopez Rangel Kevin Paul
 * Correo:  l21210392@tectijuana.edu.mx
 * Fecha:   25/10/2023
 * Curso:   Lenguajes de Interfaz, TECNM Campus ITT
 * 
 * Objetivo:
 *El objetivo de este código en Arduino IDE es crear un programa que imprima una tabla ASCII
 *que muestra los valores de bytes de caracteres ASCII en diferentes formatos. La tabla ASCII es
 *una representación de caracteres en el lenguaje de las computadoras,   *donde cada carácter se
 *asocia a un valor numérico (byte). 
 *
 * Historial de Revisiones:
 * [25/10/2023]        [Lopez Rangel Kevin Paul] - Creado
 * [25/10/2023]        [Lopez Rangel Kevin Paul] - Documentacion y subida de programas
 * 
 * Codigo proporcionado en la clase para visualizar el funcionamiento del simulador de PicoW llamado wokwi, el cual se encuentra en lenguaje C
 */

/*
  ASCII table

  Prints out byte values in all possible formats:
  - as raw binary values
  - as ASCII-encoded decimal, hex, octal, and binary values

  For more on ASCII, see http://www.asciitable.com and http://en.wikipedia.org/wiki/ASCII

  The circuit: No external hardware needed.

  created 2006
  by Nicholas Zambetti <http://www.zambetti.com>
  modified 9 Apr 2012
  by Tom Igoe

  This example code is in the public domain.

  https://www.arduino.cc/en/Tutorial/BuiltInExamples/ASCIITable
*/

void setup() {
  //Initialize serial and wait for port to open:
  Serial.begin(9600);
  while (!Serial) {
    ;  // wait for serial port to connect. Needed for native USB port only
  }

  // prints title with ending line break
  Serial.println("ASCII Table ~ Character Map");
}

// first visible ASCIIcharacter '!' is number 33:
int thisByte = 33;
// you can also write ASCII characters in single quotes.
// for example, '!' is the same as 33, so you could also use this:
// int thisByte = '!';

void loop() {
  // prints value unaltered, i.e. the raw binary version of the byte.
  // The Serial Monitor interprets all bytes as ASCII, so 33, the first number,
  // will show up as '!'
  Serial.write(thisByte);

  Serial.print(", dec: ");
  // prints value as string as an ASCII-encoded decimal (base 10).
  // Decimal is the default format for Serial.print() and Serial.println(),
  // so no modifier is needed:
  Serial.print(thisByte);
  // But you can declare the modifier for decimal if you want to.
  // this also works if you uncomment it:

  // Serial.print(thisByte, DEC);


  Serial.print(", hex: ");
  // prints value as string in hexadecimal (base 16):
  Serial.print(thisByte, HEX);

  Serial.print(", oct: ");
  // prints value as string in octal (base 8);
  Serial.print(thisByte, OCT);

  Serial.print(", bin: ");
  // prints value as string in binary (base 2) also prints ending line break:
  Serial.println(thisByte, BIN);

  // if printed last visible character '~' or 126, stop:
  if (thisByte == 126) {  // you could also use if (thisByte == '~') {
    // This loop loops forever and does nothing
    while (true) {
      continue;
    }
  }
  // go on to the next character
  thisByte++;
}
```

## Ejercicio proporcionado en el Libro en Arduino IDE
```C
/*
 * Nombre del Archivo: Ascii Table
 * Autor:   Lopez Rangel Kevin Paul
 * Correo:  l21210392@tectijuana.edu.mx
 * Fecha:   25/10/2023
 * Curso:   Lenguajes de Interfaz, TECNM Campus ITT
 * 
 * Objetivo:
 *El objetivo de este código en Arduino IDE escribir un programa que acepte 25 enteros positivos como datos y describir cada uno como impar o par
 *
 * Historial de Revisiones:
 * [25/10/2023]        [Lopez Rangel Kevin Paul] - Creado
 * [25/10/2023]        [Lopez Rangel Kevin Paul] - Documentacion y subida de programas
 * 
 * Codigo proporcionado en la clase para visualizar el funcionamiento del simulador de PicoW llamado wokwi, el cual se encuentra en lenguaje C
 */

void setup() {
  Serial.begin(9600);
}

int esPar(int num) {
  if (num % 2 == 0) {
    return 1;  // El número es par.
  } else {
    return 0;  // El número es impar.
  }
}

void loop() {
  Serial.println("Ingresa 25 números enteros positivos:");

  for (int i = 1; i <= 25; i++) {
    while (!Serial.available()) {
      // Espera a que el usuario ingrese un número.
    }
    int num = Serial.parseInt();

    if (num < 0) {
      Serial.println("Entrada no válida: El número debe ser positivo.");
      i--;  // Decrementa i para repetir la iteración actual.
    } else {
      if (esPar(num)) {
        Serial.print(num);
        Serial.println(" es par.");
      } else {
        Serial.print(num);
        Serial.println(" es impar.");
      }
    }
  }

  while (Serial.available()) {
    // Limpia el búfer de entrada serial.
    Serial.read();
  }
}
```

## Evaluacion
25%  Incluir el encabezado de nuestro templete de microcontroladores. (procure tener uno propio lo usara constatemente)

50% Corriendo el programa via el templete de WOKWI

25% Programa corriendo en su PicoW via Arduino IDE (o SDK manual de consola-powershell) o tambien VSCode

## Recursos
- "Hola Mundo" en lenguaje C en Wokwi: https://wokwi.com/projects/379538589342889985
- Ejercicio Par o Impar en Wokwi: https://wokwi.com/projects/379624675433542657
