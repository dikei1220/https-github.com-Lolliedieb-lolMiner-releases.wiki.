El "Muro de las estadísticas". Para personalizar tus estadísticas hay diferentes parámetros, sólo tienes que seleccionar lo que quieres mostrar, se requiere añadir _--statsformat_ y los campos separados por comas:

* gpuName : Nombre corto de GPU, ej. "RX 580" o "RTX 2060"
* algo : El algoritmo actual de minado. Solo visible en dual mode
* speed : Velocidad en Mhs del rig
* inflatedHr : Velocidad en Mhs inflada para comparar con los valores de los miners que inflan
* poolHr: Promedio de Mhs en Pool, dirá que tan afortunado o desafortunado eres. Si es mayor que la velocidad significa que tienes suerte si es menor estás en un momento de mala suerte. Esto llevará en mucho tiempo a lo mismo que la velocidad.
* shares: Número de soluciones enviadas. A: es el parámetro de las soluciones, S: es el de los Stales y Hw: es el de los errores de Hardware
* sharesPerMin : Número de soluciones aceptadas por minuto
* bestShare: La mejor solución encontrada
* power: Consumo de energía, normalmente en Nvidia es bastante real a los Watts de pared y en AMD es diferente dependiendo de la placa
* hrPerWatt: Eficiencia de Mhs que obtienes por 1 vatio de uso
* wattPerHr: Eficiencia de los vatios que necesitas para tener 1 Mhs
* coreclk: Reloj del núcleo en Mhz 
* memclk: Reloj de la Memoria en Mhz, que dependiendo de Nvidia o AMD se muestra diferente
* coreT: Temperatura del núcleo
* juncT: Temperatura de la unión del núcleo, esto estará disponible en todos los Polaris y más nuevos
* memT: Temperatura de la memoria, no está disponible en todas las GPUs, de momento sólo en Vega, Navi y Big Navi
* fanPct : Velocidad del ventilador en %
* speedctxc : Convierte de g/s a h/s para cortex (CTCX)
* fidelity : Cuckoo Solver Accuracy, fracción de los ciclos del grafo sobre número esperados

Por ejemplo, esto mostrará toda la información:
_--statsformat speed,poolHr,shares,sharesPerMin,bestShare,power,hrPerWatt,wattPerHr,coreclk,memclk,coreT,juncT,memT,fanPct_

![All Stats](https://i.ibb.co/g3q5R0X/allstats.jpg)


Por ejemplo, esto únicamente mostrará 6 campos seleccionados:
_--statsformat speed,poolHr,shares,sharesPerMin,hrPerWatt,wattPerHr_

![Partial Stats](https://i.ibb.co/zH5bjGB/parcialstats.jpg)

Por ejemplo, esto mostrará los siguientes campos:
_-statsformat speed,inflatedHr,poolHr,shares,sharesPerMin,bestShare,power,hrPerWatt,wattPerHr,coreclk,memclk,coreT,juncT,memT,fanPct_

![Inflated Stats](https://i.ibb.co/6tmKgVH/inflated.jpg)