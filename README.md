# templete-picow
Para trabajos de microcontroladores
[https://wokwi.com/projects/379538589342889985](https://wokwi.com/projects/379538589342889985)

# Ver el directorio de /code/ para como documentar un programa con sus pantallas, etc.

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


```
