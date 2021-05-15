**Lolminer no es reconocido como comando externo o interno**
> Ese problema aparece cuando el lolMiner.exe no está en la misma carpeta del archivo bat. Esto suele ocurrir cuando se intenta ejecutar como administrador el archivo bat o cuando el Windows Defender o el Antivirus han eliminado el lolMiner.exe. En este último caso, por favor, debe desactivar el Windows Defender o Antivirus o excluir la carpeta del lolMiner

**OC Crash**
> Normalmente el fallo de una GPU es por un overclock o undervolt extremo... Es interesante en caso de que suceda postear el error con foto y el OC en los temas.


**iGPU no funcionarán**
> Cualquier GPU integrada NO funcionará con lolMiner. Todas las GPU integradas como Intel HD620, 630, Vega 3, Vega 8, 10, ... no funcionarán con lolMiner. lolMiner necesita una GPU dedicada para funcionar.


**GPU Antiguas**
>  Cualquier GPU Nvidia anterior a Fermi/Kepler/Maxwell no funcionará como la GTX 770.


**4Gb GPUs Windows ETH**
> Ya no es posible minar en Windows con tarjetas de 4Gb, la única opción para este 4Gb es usar Linux. Además, sólo funcionará en Linux con tarjetas AMD de 4Gb en modo Zombie. La solución en Windows para 4Gb o menos es minar otros algos, como ETC, ZEL, ...

**Nvidia mitad de Hashrate**
> Este era un viejo problema ya resuelto con la versión 1.25 y superiores, con la introducción de la libería CUDA. Por favor, actualice a una versión más reciente para evitar ese problema al añadir más de 2 GPU

**Solución buqle para un crash**
> Cuando el controlador se bloquea es útil tener una solución de bucle en el archivo bat. Que automáticamente después de 10 segundos reinicie el minero. Después de la versión 1.29 la solución de bucle se aplica en todos los algoritmos. Por favor, intente estar actualizado. 

 
**Caracteres extraños en la consola**
> Eso suele ocurrir por intentar mostrar la consola con colores, si eso ocurre solo hay que añadir el parámetro --nocolor en la vía de configuración. Eso te permitirá verla sin esos caracteres.

**Zombie Mode y Nvidia**
> Ya no es posible minar en Windows o Linux con tarjetas Nvidia de 4Gb. El modo Zombie solo funciona en Linux para las tarjetas AMD 4Gb. La solución para las tarjetas Nvidia de 4Gb o menos es minar otros algos, como ETC, ZEL, ...

