Para fijar los Mhz de clock el límite de potencia, no es necesario fijarlo. Si especifica un límite de potencia y es demasiado bajo, el reloj no se podrá fijar. Así que es una buena recomendación poner un límite de potencia alto y reducir los vatios con la solución de fijación del reloj. Solo para Turing y Ampere:

_Linux:_

**HiveOS:** Hay que poner el valor directo en el +Core Clock Mhz, en este ejemplo serán 750Mhz a una RTX 3070. Solo disponible a partir de 0.6-202@210331

<a href="https://ibb.co/4SnJJxs"><img src="https://i.ibb.co/YdFbbGD/HiveOS.jpg" alt="HiveOS" border="0"></a>

**MMPOS:** En Settings hay que seleccionar 'Lock GPU clock frequency`, en este ejemplo serán 750Mhz a una RTX 3070

<a href="https://ibb.co/2ybwzMv"><img src="https://i.ibb.co/s2BhT1K/MMPOS.jpg" alt="MMPOS" border="0"></a>

**RaveOS:** En Set hay que especificar este parámetro: `oc --fixclk=value`, en este ejemplo serán 750Mhz a una RTX 3070

<a href="https://ibb.co/zFBSNQP"><img src="https://i.ibb.co/m02HSbh/RaveOS.jpg" alt="RaveOS" border="0"></a>

**SMOS:** Se necesita hacer a través del bash command, hay que especificar el parámetro:`sudo nvidia-smi -i $GPU -lgc $VALUE` . Recordar hay que usar la web base64encode.org para convertirlo.


_Windows 10:_

**Msi Afterburner:**
1. Puede establecer una curva V/F plana utilizando el MSI Afterburner.
1. Arrastre el deslizador del reloj del núcleo hasta la izquierda.
1. Pulsa aplicar.
1. Ctrl + F para abrir la curva V/F.
1. Busque el voltaje que desea ejecutar y arrástrelo hasta la frecuencia que desea ejecutar.
1. Pulsa aplicar y todo lo que está a la derecha del punto seleccionado debería aplanarse.

CTRL + F: abre el menú de la curva de tensión

CTRL + L: bloquea el voltaje y la frecuencia en el punto resaltado

Tab / Shift-Tab: selecciona el punto siguiente/anterior

CTRL + ARRIBA / CTRL + ABAJO: aumenta/disminuye la frecuencia del punto seleccionado en 10 (sería 1 sin ctrl)

**Manualmente**: Esto funciona en _Linux_ y en _Windows 10_ `nvidia-smi -i $GPU -lgc $VALUE`

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

(1) Windows con 470.05 Drivers