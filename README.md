# templete-picow
Para trabajos de microcontroladores
[https://wokwi.com/projects/379515466942050305](https://wokwi.com/projects/379515466942050305)

# Ver el directorio de /code/ para como documentar un programa con sus pantallas, etc.

```C
/*
 * Nombre del Archivo: Hola Mundo.c
 * Autor:   [Lopez Rangel Kevin Paul]
 * Correo:  [l21210392@tectijuana.edu.mx]
 * Fecha:   [24/10/2023]
 * Curso:   Lenguajes de Interfaz, TECNM Campus ITT
 * 
 * Objetivo:
 * Este programa está diseñado para [programar el Hola Mundo a traves del Simulador PicoW].
 *
 * Historial de Revisiones:
 * [Fecha]        [Tu Nombre] - Creado
 * [Fecha]        [Tu Nombre] - Actualizado para añadir [característica/corrección]
 *
 */

#include <stdio.h>
#include "pico/stdlib.h"

int main() {
  stdio_init_all();
  while (true) {
    printf("Hola, Mundo!\n");
    sleep_ms(250);
  }
}

```
