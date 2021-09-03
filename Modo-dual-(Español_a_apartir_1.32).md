Minar ZIL&ETH o ZIL&ETC en diferentes pools
Normalmente, al minar ZIL necesitas minar ETH en la misma pool o necesitas confiar en un solución de reenvío de proxy de pool implementado por la pool. El primer caso restringe tu minado a una única pool mientras que el segundo puede tener la gran desventaja de una peor latencia de minería de ETH o inestabilidades de reenvío de pool. A partir de lolMiner 1.32 y superiores permiten evitar esta situación añadiendo una segunda conexión de stratum que recogerá tus shares de ETH (o ETC) y las llevará directamente al pool que quieras, mientras que los shares de ZIL serán enviados durante los momentos de minado de ZIL al pool de ZIL.

Para configurar esto sigue los siguientes pasos:

a) Configurar la pool ETH o ETC de forma normal. En caso de quieres utilizar ETC+ZIL selecciona ETCHASH como parámetro del algoritmo. La configuración debe ser completa.

b) Añada el parámetro --dualmode zil --dualpool *pool_of_zil* --dualuser *data_for_the_zil_pool* --dualpass *password_for_the_zil_pool* a sus argumentos de línea de comandos o a sus parámetros de usuario adicionales. Sustituya aquí los elementos de *pool_of_zil*, *data_for_the_zil_pool* y *password_for_the_zil_pool* por sus valores deseados de minería ZIL.

Ahora el minero creará ambas conexiones al iniciarse, pero minará shares ZIL en la conexión extra, que puede ser diferente a la primera, que sólo se utilizará cuando se mine ETH o ETC.

Tener en cuenta que para activar automáticamente el modo de caché ZIL en tus tarjetas de 6 Gb y 8 Gb hay que añadir el parámetro --enablezilcache

Ejemplos:

* _lolMiner --algo ETHASH --pool eth.2miners.com:2020 --user 0x155da78b788ab54bea1340c10a5422a8ae88142f.workerName --enablezilcache --dualmode zil --dualpool eu1-zil.shardpool.io:3333 --dualuser 0x155da78b788ab54bea1340c10a5422a8ae88142f.workerName --dualpass zil12kfcrls87pzqnneratejhk8xa3wdzlhrdl7w5g@eth.2miners.com:2020_

* _lolMiner --algo ETHASH --pool eu-eth.2miners.com:2020 --user 0x155da78b788ab54bea1340c10a5422a8ae88142f.workerName --enablezilcache --dualmode zil --dualpool eu-zil.rustpool.xyz:8008 --dualuser 0x155da78b788ab54bea1340c10a5422a8ae88142f --dualpass zil12kfcrls87pzqnneratejhk8xa3wdzlhrdl7w5g@eth.2miners.com:2020@4G_

* _lolMiner --algo ETHASH --pool eth.2miners.com:2020 --user 0x155da78b788ab54bea1340c10a5422a8ae88142f.workerName --enablezilcache --dualmode zil --dualpool eu.ethash.k1pool.com:5000 --dualuser KrSv2Z38HuG4fkJBiP4QgYE6osoFfUECmD7_

* _lolMiner --algo ETHASH --pool eth.2miners.com:2020 --user 0x155da78b788ab54bea1340c10a5422a8ae88142f --enablezilcache --dualmode zil --dualpool eu.ezil.me:5555 --dualuser 0x155da78b788ab54bea1340c10a5422a8ae88142f.zil1qxl9lwat8rvf3lkn4fluexzh9pwemn0x94nn5a_