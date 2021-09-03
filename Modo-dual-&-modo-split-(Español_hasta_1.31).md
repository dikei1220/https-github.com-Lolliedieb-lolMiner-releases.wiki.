## Modo dual & modo split

### Caso A: Minar ZIL&ETH o ZIL&ETC en diferentes pools

Normalmente, al minar ZIL necesitas minar ETH en la misma pool o necesitas confiar en un solución de reenvío de proxy de pool implementado por la pool. El primer caso restringe tu minado a una única pool mientras que el segundo puede tener la gran desventaja de una peor latencia de minería de ETH o inestabilidades de reenvío de pool. lolMiner 1.20 y superiores permiten evitar esta situación añadiendo una segunda conexión de stratum que recogerá tus shares de ETH (o ETC) y las llevará directamente al pool que quieras, mientras que los shares de ZIL serán enviados durante los monetos de minado de ZIL al pool de ZIL.

Para configurar esto sigue los siguientes pasos:



* a) Configurar la pool ZIL de forma normal. En caso de quieres utilizar ETC+ZIL selecciona ETCHASH como parámetro del algoritmo. La configuración debe ser completa, es decir, si se detiene después de este punto debe utilizar la minería dual normal ZIL+ETH o ZIL+ETC como está acostumbrado. 

* b) Añada el parámetro --dualmode zil --dualstratum ETHWALLET.ETHWORKER@ETHPOOL:ETHPORT a sus argumentos de línea de comandos o a sus parámetros de usuario adicionales. Sustituya aquí los elementos de ETHWALLET, ETHWORKER, ETHPOOL y ETHPORT y por sus valores deseados de minería ETH/ETC. Tener en cuenta que entiende los prefijos como "tls://" para activar ssl en la conexión de stratum adicional.


Ahora el minero creará ambas conexiones al iniciarse, pero minará shares ETH (o ETC) en la conexión extra, que puede ser diferente a la primera, que sólo se utilizará cuando se mine ZIL. 

Tener en cuenta que para activar automáticamente el modo de caché ZIL en tus tarjetas de 6 Gb y 8 Gb hay que añadir el parámetro _--enablezilcache_

Ejemplos:

* Shardpool.io: `lolMiner --algo ETHASH --pool eu1-zil.shardpool.io:3333 --user 0x155da78b788ab54bea1340c10a5422a8ae88142f.workerName --pass zil12kfcrls87pzqnneratejhk8xa3wdzlhrdl7w5g@eth.2miners.com:2020@ --enablezilcache --dualmode zil --dualstratum 0x155da78b788ab54bea1340c10a5422a8ae88142f@eth.2miners.com:2020`

* rustpool.xyz:`lolMiner --algo ETHASH --pool eu-zil.rustpool.xyz:8008 --user 0x155da78b788ab54bea1340c10a5422a8ae88142f --pass zil12kfcrls87pzqnneratejhk8xa3wdzlhrdl7w5g@eth.2miners.com:2020@4G --worker workerName --enablezilcache --dualmode zil --dualstratum 0x155da78b788ab54bea1340c10a5422a8ae88142f@eth.2miners.com:2020`

* k1pool.com: `lolMiner --algo ETHASH --pool eu.ethash.k1pool.com:5000 --user K1LOGIN.workerName --enablezilcache --dualmode zil --dualstratum 0x155da78b788ab54bea1340c10a5422a8ae88142f@eth.2miners.com:2020`

* ezil.me: `lolMiner --algo ETHASH --pool eu.ezil.me:5555 --user 0x155da78b788ab54bea1340c10a5422a8ae88142f.zil12kfcrls87pzqnneratejhk8xa3wdzlhrdl7w5g --worker workerName --enablezilcache --dualmode zil --dualstratum 0x155da78b788ab54bea1340c10a5422a8ae88142f@eth.2miners.com:2020`



### Caso B: Minar ETH en tarjetas de 8G mientras se mina ETC en tarjetas de 4G


Normalmente los mineros permiten usar sólo un algoritmo a la vez. Con lolMiner 1.20 el minero es capaz de soportar la creación de dos conexiones a tus pools favoritos y minar dos algoritmos dentro del mismo minero. Concretamente este modo ha sido construido para minar ETCHASH en algunos GPUS de 4Gb mientras otros se quedan en ETH.

Para configurarlo sigue los siguientes pasos:

* a) Configure su minero de ETH de forma normal, no se requiere ninguna otra configuración. 
* b) Añada los parámetros --dualmode etc --dualstratum ETCWALLET.ETCWORKER@ETCPOOL:ETCPORT a sus argumentos de línea de comandos o a sus parámetros extra de usuario. Sustituya aquí los elementos de ETCWALLET, ETCWORKER, ETCPOOL and ETCPORT y por sus valores deseados de minería ETC. Tener en cuenta que entiende prefijos como "tls://" para activar ssl en la conexión de stratum adicional.
* c) (Opcionalmente) Puede utilizar --dualdevices para seleccionar aquellos dispositivos que minarán ETC en lugar de ETH. Por defecto, todas las tarjetas 3Gb y 4Gb minaran al algoritmo secundario (ETC), mientras que el resto de tarjetas permanecerán en el primario (ETH). El parámetro lee una lista de números separados por comas, que tiene que ser el subconjunto de los tarjetas que se están ejecutando. Por ejemplo, la combinación de --devices 0,1,2,4,5 --dualdevices 4,5 hará que las tarjetas 0,1 y 2 minen el primer algoritmo, las tarjetas 4 y 5 el segundo algoritmo y la tarjeta 3 se salta el minado.

Ejemplo:
ETH + ETC: lolMiner --algo ETHASH --pool $POOL --user $ETHWALLET.$ETHWORKER --worker $WORKER  --dualmode etc --dualstratum ETCWALLET.ETCWORKER@ETCPOOL:ETCPORT 

### Caso de uso C: Minar ETH/ETC en dos pools diferentes

Normalmente los mineros permiten usar sólo la minería en un pool a la vez. Con lolMiner 1.25 el minero empieza a soportar la creación de dos conexiones a tus pools favoritos y minar ETH/ETC dentro de la misma instancia del minero. Concretamente este modo fue construido para minar para compartir RIGS. 

Para configurarlo sigue los siguientes pasos:

 * a) Configure su minado de ETH/ETC de forma normal, no se requieren más ajustes.
 * b1) Añada los parámetros para ETH: --dualmode eth --dualstratum *ETHWALLET*.*ETHWORKER*@*ETHPOOL*:*ETHPORT* a sus argumentos de línea de comandos o a sus parámetros de usuario adicionales. Sustituya aquí los elementos de *ETHWALLET*, *ETHWORKER*, *ETHPOOL* y *ETHPORT* por sus credenciales de minería ETH deseadas. Tenga en cuenta que <ETHSTRATUM> entiende prefijos como "tls://" para activar ssl en la conexión del estrato adicional.
 * b2) Añade los parámetros para ETC: --dualmode etc --dualstratum *ETCWALLET*.*ETCWORKER*@*ETCPOOL*:*ETCPORT* a sus argumentos de línea de comandos o a sus parámetros de usuario adicionales. Sustituya aquí los elementos de *ETCWALLET*, *ETCWORKER*, *ETCPOOL* y *ETCPORT* por sus credenciales de minería ETC deseadas. Tenga en cuenta que <ETCSTRATUM> entiende prefijos como "tls://" para activar ssl en la conexión del estrato adicional.
 * c) Ahora tienes que seleccionar qué dispositivos usar en cada conexión, con --dualdevices seleccionarás con GPU minar en el 2º pool, mientras que las otras tarjetas se quedan en el primario. El parámetro toma una lista de números separados por comas, que tiene que ser un subconjunto de los dispositivos que se ejecutan. Por ejemplo, la combinación de --devices 0,1,2,4,5 --dualdevices 4,5 hará que las tarjetas 0,1 y 2 minen en el primer pool, las tarjetas 4 y 5 en el segundo pool y la tarjeta 3 no minará. 


