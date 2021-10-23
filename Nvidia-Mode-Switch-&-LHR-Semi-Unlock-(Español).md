# Esto es recomendado para la versión 1.32a. Las nuevas versiones ya lo hacen automáticamente.
# --mode switch en GPUs Nvidia (también para el control de LHR)
--mode controla el kernel cargado y los modos de operación para las GPUs Nvidia. Las tarjetas AMD actualmente ignoran este parámetro por completo. Puedes establecer un valor para todo el equipo o proporcionar una lista de valores separados por comas para obtener modos individuales para cada tarjeta. Las tarjetas AMD pueden usar cualquier valor por el momento. 

## --mode a:
Este modo es habitualmente el más rápido cuando no se aplica ningún limite de potencia. Normalmente da mejor rendimiento en las RTX 3080 and 3090, pero no así en las GPUs de gama baja. Este modo es cuando el precio de la electricidad no es un problema.

## --mode b (defecto):
Este es el modo por defecto con optimización de energía. Normalmente la mejor opción para todas las No-LHR Nvidia GPUs y la RTX 3060 LHR V1 en el driver 470.05 beta de Windows .

## --mode LHR1:
Este modo es el por defecto para las RTX 3060 LHR v1 en Linux cuando el driver de Nvidia entre 455.45.01 y 460.39. Esto da hasta el 80% del performance de la tarjeta. En el caso que se use otro driver distinto se usará el modo LHR2 explicado a continuación.

## --mode LHR2: 
Este modo es el que está por defecto para las LHR (v2) Nvidia RTX 3000 . El performance está aproximadamente entre 67–71% del potencial de la tarjeta.

## --mode LHRLP: 
Este modo es el recomendado cuando se usa Fixed Core por debajo de los siguientes valores de la tabla:

| GPU        |  3060  | 3060 Ti | 3070 | 3070 Ti | 3080 | 3080 Ti |
| ------------- |---------:|---------:|---------:|---------:| ---------:|---------:|  
| Max core | 1150 Mhz | 1150 Mhz | 855 Mhz | 855 Mhz | 1050 Mhz | 1150 Mhz |

Con estos cores bajos la eficiencia suele ser generalmente inferior, pero los parámetros de semidesbloqueo de LHR permiten dar una mayor parte del potencial que tiene la GPU. Por lo tanto, a menos que ejecute mucho más alto núcleo a menudo puede ser una buena idea, bajar el reloj del núcleo a los límites indicados anteriormente.

Nota: ¡Este es el modo recomendado para todos los 3080 y 3080ti!

## Tuning

--lhrtune este parámetro permite afinar más cada tarjeta dentro del rig. Permite valores positivos y valores negativos, y permites valores diferentes para cada gráfica.

* Valores positivos se incrementan los Mhs pero se incrementa el riesgo de que la tarjeta active el bloque LHR y haya que esperar 1 minuto para volver a minar.

* Valores negativos se reducen los Mhs pero se reduce también el riesgo de bloqueo LHR

Habitualmente para conseguir el mejor tuneo, es una vez tenemos puesto un Fix Core con el modo LHRLP o LHR2 se añade el --lhrtune 5. E iremos haciendo incrementos de 5, dejando como mínimo unos 20 minutos para ver si hay algún bloqueo LHR. Si no se bloquea podemos incrementar otros 5, y repetimos el test de 20 minutos, así sucesivamente hasta que llegue un momento que bloquea. Cuando eso sucede volvemos al estado que no bloqueaba. Si todavía queremos maximizar los Mhs podemos hacer pequeños incrementos de 15 en 15 del Core. Repitiendo el proceso sobre el valor lhrtune estable.

Si nuestra tarjeta se nos bloquea haremos el proceso inverso, empezamos por --lhrtune -5, e iremos haciento test de 20 minutos hasta asegurar que es estable, si se bloquea bajaremos otros -5, y así secusivamente hasta tener un valor estable, donde podemos luego practicar el incremento del Core en escalones de 15 en 15.


## Ejemplos

_--mode LHR2 --lhrtune 10,5,-15,15,15,15_ que aplicará a todos los rig el modo LHR2 y a la GPU0 el modo 10, a la GPU1 el modo 5, a la GPU2 el modo -15, y a la GPU 3/4/5 el modo 15

_--mode b,b,b,LHRLP,b,b,b --lhrtune -3_ que aplicará el modo b a todos los rigs excepto a la GPU3 que usará el modo LHRLP, el valor de tune sólo afectará a todos los mode LHR2 or LHRLP, en este caso el LHRLP con un valor de tune de -3.
