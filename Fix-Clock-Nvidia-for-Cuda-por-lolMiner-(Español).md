Para fijar el reloj de la tarjeta gráfica usando directamente lolMiner, esto está únicamente disponible para Nvidia Turing y Ampere. Recordar que los pasos del Core Clock son de 15Mhz en 15Mhz.

Esto únicamente se aplicará si el Límite de Potencia es lo suficientemente alto para la carga a la misma.
 
Solo hay que usar --cclk separado por comas. * se utiliza para omitir la GPU. 

--cclk * ,* ,* ,855,* ,* ,* ,* 

That will apply 855 Core Fix to GPU 3

![Core Fix ](https://i.ibb.co/6tmKgVH/inflated.jpg)


Values: 
| GPU        | Range       | 
| ------------- |:-------------:| 
| 2060 | 1000 - 1050 |
| 2070 | 1000 - 1050 |
| 2080 | 1110 - 1160 |
| 3060 (1) | 1070 - 1120 |
| 3060ti | 1320 - 1370 |
| 3070 | 735 - 785 |
| 3080 | 1010 - 1060 |
| 3090 | 1120 - 1170 |

_Note: Very high Memory OC need higher Clock_

(1) Windows with 470.05 Drivers