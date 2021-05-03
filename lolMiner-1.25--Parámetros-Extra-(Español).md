## Parámetros extra (Dual Mining, Worker, Modo Zombie, Dual Kernel CUDA, ...)

**--worker arg** arg le permitirá especificar el nombre del trabajador de su equipo.

**--devices arg** arg te permite seleccionar las GPU a usar separadas por commas como _--devices 0,1,3,4_ solo seleccionar las GPU 0,1,3,4 y saltará la 2


**--dualmode arg** arg = `zil` or `etc`. Modo dual utilizado. Opciones permitidas: 

**--dualmode zil** se minará ETH o ETC con ZIL. se recomienda añadir el parámetro **--enablezilcache**, para activar la caché ZIL para un intercambio rápido, entre ETH/ETC y ZIL. Ejemplos :

* Shardpool.io: `lolMiner --algo ETHASH --pool eu1-zil.shardpool.io:3333 --user 0x155da78b788ab54bea1340c10a5422a8ae88142f.workerName --pass zil12kfcrls87pzqnneratejhk8xa3wdzlhrdl7w5g@eth.2miners.com:2020@ --enablezilcache --dualmode zil --dualstratum 0x155da78b788ab54bea1340c10a5422a8ae88142f@eth.2miners.com:2020`

* rustpool.xyz:`lolMiner --algo ETHASH --pool eu-zil.rustpool.xyz:8008 --user 0x155da78b788ab54bea1340c10a5422a8ae88142f --pass 0x155da78b788ab54bea1340c10a5422a8ae88142f@eth.2miners.com:2020@4G --worker workerName --enablezilcache --dualmode zil --dualstratum 0x155da78b788ab54bea1340c10a5422a8ae88142f@eth.2miners.com:2020`

* k1pool.com: `lolMiner --algo ETHASH --pool eu.ethash.k1pool.com:5000 --user K1LOGIN.workerName --enablezilcache --dualmode zil --dualstratum 0x155da78b788ab54bea1340c10a5422a8ae88142f@eth.2miners.com:2020`

* ezil.me: `lolMiner --algo ETHASH --pool eu.ezil.me:5555 --user 0x155da78b788ab54bea1340c10a5422a8ae88142f.zil12kfcrls87pzqnneratejhk8xa3wdzlhrdl7w5g --worker workerName --enablezilcache --dualmode zil --dualstratum 0x155da78b788ab54bea1340c10a5422a8ae88142f@eth.2miners.com:2020`

**--dualmode etc** minará ETH en tarjetas de 8G mientras que minará ETC en tarjetas de 4G. Ejemplos:`lolMiner --algo ETHASH --pool eth.2miners.com:2020 --user 0x155da78b788ab54bea1340c10a5422a8ae88142f --dualmode etc --dualstratum 0x155da78b788ab54bea1340c10a5422a8ae88142f@etc.2miners.com:1010`

**--ethstratum arg** arg = `ETHPROXY` or `ETHV1`, selecciona el stratum de Ethash. Opciones disponibles: `ETHPROXY`: Ethereum Proxy y `ETHV1`: EthereumStratum/1.0.0 (Nicehash), cuando estés minando en modo dual, puedes seleccionar `--ethstratum ETHPROXY,ETHV1`, eso hará que la 2ª conexión el ETH o ETC utilice la conexión Nicehash. Útil para minar en modo dual ETH + ZIL cuando el pool de ETH es Nicehash.

**--4g-alloc-size arg** arg establece el tamaño del DAG (en MByte) que el minero puede utilizar en las tarjetas 4G. Puede ser una lista de valores separados por comas para cada tarjeta. Valores sugeridos en Linux: 4080, 4078, 4076, 4074, 4072, 4070, 4068, 4064, 4062. Cuanto más alto sea el valor, mayor será el rendimiento.

**--zombie-tune arg**  arg establece el modo Zombie, puede ser `auto` o valores de `0 a 16` Cuando se ejecuta el modo Zombie una vez terminado informará del valor óptimo, por lo que puede ser utilizado como un parámetro la próxima vez, evitando el tiempo de sintonía automática. Ejemplo:
* Primera ejecución, con --4g-alloc-size 4080.
`lolMiner --algo ETHASH --pool eth.2miners.com:2020 --user 0x155da78b788ab54bea1340c10a5422a8ae88142f.WorkerName --4g-alloc-size 4080 --zombie-tune auto`

* Cuando se tiene el valor Zombie-tune, usaremos para el ejemplo 15.25 y --4g-alloc-size 4080 :
`lolMiner --algo ETHASH --pool eth.2miners.com:2020 --user 0x155da78b788ab54bea1340c10a5422a8ae88142f.WorkerName --4g-alloc-size 4080 --zombie-tune 15.25`

**--mode arg** arg puede ser `a` o `b`. `b` es viene por defecto, un kernel de bajos Watts para minar con gráficas Nvidia con CUDA. Puede tener valores separados por comas para configurar múltiples tarjetas de forma diferente. El modo `a` maximiza las Mhs y el modo `b` obtiene menos Mhs pero con una mejora de importación en Watts y la temperatura de la tarjeta. Este modo en particular tiene que ser usado en combinación con Fix Clock. Nota: Las tarjetas AMD deben ser `a`. Ejemplo:

`lolMiner --algo ETHASH --pool eth.2miners.com:2020 --user 0x155da78b788ab54bea1340c10a5422a8ae88142f.WorkerName --mode a,b,b,a,a`

Eso seleccionará para la GPU 0,3,4 el Modo Kernel `a` y la GPU 1,2 será `b`.