
Esta página describe cómo iniciar el minero lolMiner 1.25 y posteriores.

Para una lista detallada de más parámetros de lolMiner puedes consultar `lolMiner -h`.

## Parámetros básicos en la línea de comandos

Hay tres cosas que lolMiner necesita saber en cualquier caso para empezar a minar, son:

- el algoritmo a minar
- la dirección del pool o nodo solitario al que conectarse
- el nombre de usuario / cartera para minar

### Configurar el algoritmo a minar

Hay dos maneras en lolMiner de especificar el algoritmo que quieres minar. Tienes que elegir **una** de ellas para empezar a minar.

La primera opción es **--algo (-a)** seguido de uno de los siguientes nombres de algoritmos

Parámetro | Algoritmo
| ------------- | ------------- |
| AUTOLYKOS2 | Autolykos V2  |
| BEAM-III | BeamHash III |
| C29AE   | Cuckoo 29  |
| C29D  | CuckarooD 29  |
| C29M | CuckarooM 29 |
| C30CTX | Cuckaroo 30 Cortex |
| C31 | Cuckatoo 31   |
| C32 | Cuckatoo 32   |
| CR29-32   | Cuckaroo 29-32  |
| CR29-40  | Cuckaroo 29-40  |
| CR29-48 | Cuckaroo 29-48 |
| EQUI144_5 | Equihash 144/5  |
| EQUI192_7 | Equihash 192/7  |
| EQUI210_9 | Equihash 210/9  |
| ETCHASH | Etchash  |
| ETHASH | Ethash   |
| ZEL | ZelHash |

Tenga en cuenta que siempre puede llamar a `lolMiner --list-algos` para obtener una lista de todos los algoritmos soportados, así como la Fee. También la lista le informará si los algoritmos soportan/requieren la opción de personalización (--pers) que se requiere para algunos de los algoritmos de Equihash.

La segunda forma de configurar lolMiner es a través del parámetro **--coin (-c)**. Este parámetro establece una configuración más detallada para los perfiles seleccionados y permite funciones especiales, por ejemplo, conmutadores de algoritmos o la combinación de un algoritmo con la personalización adecuada.

Las entradas disponibles para --coin son:

Parámetro | Descripción
| ------------- | ------------- |
| AION | Seleccionar Equihash 210/9 and right settings to Minar Aion |
| AUTO144_5 | Minar Equihash 144/5 y permitir a la pool la personalización |
| AUTO192_7 | Minar Equihash 192/7 y permitir a la pool la personalización |
| BEAM | Minar Beam and switch algorithm on Beam Hash II / III fork height |
| BTCZ | Minar Equihash 144/5 con personalización BitcoinZ  |
| BTG  | Minar Equihash 144/5 con personalización Bitcoin Gold  |
|ETC | Seleccionar parámetros & stratum para minar Ethereum Classic |
|ETH | Seleccionar parámetros & stratum para minar Ethereum |
|CTXC | Seleccionar parámetros & stratum para minar Cortex Ai |
|EXCC | Seleccionar parámetros & stratum para minar Exchange Coin |
|GRIN-C29M | Seleccionar parámetros & stratum para minar Grin C29 |
|GRIN-C32  | Seleccionar parámetros & stratum para minar Grin C32 |
|MWC-C29D  | Seleccionar parámetros & stratum para minar MWC C29 |
|MWC-C31  | Seleccionar parámetros & stratum para minar MWC C31 |
|XSG | Minar Equihash 144/5 con personalización Snow Gem |
|YEC | Minar Equihash 192/7 con personalización YCash |
|ZCL | Minar Equihash 192/7 con personalización Zclassic |
|ZEL | Minar Zelhash & stratum to Minar FLUX (ZEL) |
|ZER  | Minar Equihash 192/7 con personalización Zero |

Tenga en cuenta que siempre puede llamar a `lolMiner --list-coins` para obtener una lista de todas las configuraciones de monedas soportadas, así como la Fee.

### Dar la dirección de la pool, el puerto y el nombre de usuario / cartera para minar en.

El parámetro para seleccionar el pool de minería al que conectarse viene dado por **--pool**. Tenga en cuenta que esta opción toma la dirección así como el puerto en el formato `<dirección del pool>:<puerto del pool>`.

El nombre de usuario o el monedero se pasarán con el parámetro **--user**. En caso de que su pool requiera una contraseña para iniciar sesión, puede añadir el parámetro opcional **--pass**.

**Para configurar pools de conmutación por error** las opciones --pool --user y --pass pueden ser pasadas varias veces al minero. Serán procesadas en orden, por lo que la primera ocurrencia pertenece a la conexión primaria, la segunda a la primera conmutación por error y así sucesivamente. Cuando el minero pierde la conexión con el pool primario con demasiada frecuencia (5 veces en un periodo corto de tiempo), intentará conectarse con el segundo conjunto de credenciales.

## Ejemplos de una línea

Comienza a minar ETH en el pool de 2miners:

`lolMiner --algo ETHASH --pool eth.2miners.com:2020 --user 0x155da78b788ab54bea1340c10a5422a8ae88142f.WorkerName`

Comienza a minar ETC en el pool de 2miners:

`lolMiner --algo ETCHASH --pool etc.2miners.com:1010 --user 0x155da78b788ab54bea1340c10a5422a8ae88142f.WorkerName`

Comienza a minar  Beam automatic Beam Hash II / III en sunpool

`lolMiner --coin BEAM --pool beam.sunpool.top:3334 --user 32f2e8765c2e8f5ea41becc5f397024c94d80cc5fc50ee917af23b260ecb3a5f.workerName`

Comienza a minar  Grin-C32 en 2Miners pool

`lolMiner -a C32 --pool asia-grin.2miners.com:3030 --user 2aHR0cHM6Ly9ncmluLmJpdG1lc2guY29tL3d1Q3BLeW5kVllZanFQQm1ldHRCNWJjMjE2.workerName`

o

`lolMiner --coin GRIN-C32 --pool asia-grin.2miners.com:3030 --user 2aHR0cHM6Ly9ncmluLmJpdG1lc2guY29tL3d1Q3BLeW5kVllZanFQQm1ldHRCNWJjMjE2.workerName`

Comienza a minar  BeamHash I with personalization para DEFIs en sunpool:

`lolMiner -a BEAM-I --pers GrimmPOW --pool defis.sunpool.top:3334 --user 32f2e8765c2e8f5ea41becc5f397024c94d80cc5fc50ee917af23b260ecb3a5f.workerName`


