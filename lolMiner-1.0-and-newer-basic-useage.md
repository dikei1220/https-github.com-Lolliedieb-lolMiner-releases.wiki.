This page describes to start basic mining parameters for lolMiner 1.0 and newer. For a detailed list of more lolMiner parameters you can check `lolMiner -h`.

## Basic parameters in command line


**--devices arg** arg has to be devices number separated by commas like _--devices 0,1,3,4_ will select GPU 0,1,3,4 and skip 2 or AMD or NVIDIA

**--tstop** to stop any mining operation on a GPU at the given temperature.  _--tstop 75_ Will stop mining that GPU at 75C

**--tstart** to allow a restart of the card below a lower temperature _--tstart 50_ Will restart mining that GPU at 50C

**--tmode edge/junction/memory** to apply the scheme to edge (chip), junction (hotspot) or memory temperature. If a GPU does not have the required sensors the chip temperature will be used as a back up - if no sensors are available at all the parameters will be ignored.

**--statsformat extended** it is a fast way to show a nice wall of stats

**--dagdelay [=arg(=0)]** (=-1) Delay between creating the DAG buffers for the GPUs. Negative values enable parallel generation (default).

**--cclk arg (=*)** The core clock used for the NVidia GPUs, cards are separated with a comma. "*" can be used to skip a card. Only for Nvidia Ampere and Turing

**--watchdog off/exit/script**  The options are:

_off_ this will do nothing except for printing a message. If only a single card did crash and not the whole driver this means the other cards will continue mining.

_exit_ this will close the miner with a exit code of 42. This can be picked up by the .sh or .bat script that did start the miner (an example is provided in mine_eth.sh and mine_eth.bat) so the miner will restart after some seconds of pause. This is recommended option for Nvidia cards.

_script_ With this option the miner will call an external script (default path is current working directory and there emergency.sh / .bat), which can be configured with --watchdogscript. The moment the script is called the miner itself will exit. The script needs to take care about rebooting the rig or informing the OS what to do. Since this was the default behavior in previous versions it also is the default. In case the script can not be found, an error will be printed and the miner will continue as with --watchdog off.

**--enablezilcache** that will enable a cache for a fast swap in the dual mining

**--dualmode arg** where arg = zil or etc. Dual mode used. Allowed options:

**--dualmode zil** will mine ETH or ETC with ZIL. it is recommened to add the parameter --enablezilcache, to enable ZIL cache for a fast swap, between ETH/ETC and ZIL. Examples :

Shardpool.io: _lolMiner --algo ETHASH --pool eu1-zil.shardpool.io:3333 --user 0x155da78b788ab54bea1340c10a5422a8ae88142f.workerName --pass zil12kfcrls87pzqnneratejhk8xa3wdzlhrdl7w5g@eth.2miners.com:2020@ --enablezilcache --dualmode zil --dualstratum 0x155da78b788ab54bea1340c10a5422a8ae88142f@eth.2miners.com:2020_

rustpool.xyz: _lolMiner --algo ETHASH --pool eu-zil.rustpool.xyz:8008 --user 0x155da78b788ab54bea1340c10a5422a8ae88142f --pass 0x155da78b788ab54bea1340c10a5422a8ae88142f@eth.2miners.com:2020@4G --worker workerName --enablezilcache --dualmode zil --dualstratum 0x155da78b788ab54bea1340c10a5422a8ae88142f@eth.2miners.com:2020_

k1pool.com: _lolMiner --algo ETHASH --pool eu.ethash.k1pool.com:5000 --user K1LOGIN.workerName --enablezilcache --dualmode zil --dualstratum 0x155da78b788ab54bea1340c10a5422a8ae88142f@eth.2miners.com:2020_

ezil.me: _lolMiner --algo ETHASH --pool eu.ezil.me:5555 --user 0x155da78b788ab54bea1340c10a5422a8ae88142f.zil12kfcrls87pzqnneratejhk8xa3wdzlhrdl7w5g --worker workerName --enablezilcache --dualmode zil --dualstratum 0x155da78b788ab54bea1340c10a5422a8ae88142f@eth.2miners.com:2020_

**--dualmode etc** will mine Mine ETH on 8G cards while mining ETC on 4G cards. Examples :_lolMiner --algo ETHASH --pool eth.2miners.com:2020 --user 0x155da78b788ab54bea1340c10a5422a8ae88142f --dualmode etc --dualstratum 0x155da78b788ab54bea1340c10a5422a8ae88142f@etc.2miners.com:1010_

**--ethstratum arg** where arg = ETHPROXY or ETHV1, this Ethash stratum mode. Available options: ETHPROXY: Ethereum Proxy and ETHV1: EthereumStratum/1.0.0 (Nicehash), when you are mining in dual mode, you can select --ethstratum ETHPROXY,ETHV1, that will make that the 2nd connection the ETH or ETC will use the Nicehash connection. Useful to mine dual mining ETH + ZIL when the ETH pool is Nicehash.

**--4g-alloc-size arg** where arg sets the DAG size (in MByte) the miner is allowed to use on 4G cards. Can be a comma separated list of values for each card. Suggested values in Linux: 4080, 4078, 4076, 4074, 4072, 4070, 4068, 4064, 4062. The higher value the most performance.

**--zombie-tune arg** where arg sets the Zombie tune mode, it can be auto or values from 0-16. When Zombie Mode is run it will inform after the auto tune, which is the optimal values, so it can be used as a parameter next time, avoiding the autotune time. Example:

First time run, with _--4g-alloc-size 4080_. lolMiner --algo ETHASH --pool eth.2miners.com:2020 --user 0x155da78b788ab54bea1340c10a5422a8ae88142f.WorkerName --4g-alloc-size 4080 --zombie-tune auto

When you have the Zombie-tune Value and _--4g-alloc-size 4080_ : lolMiner --algo ETHASH --pool eth.2miners.com:2020 --user 0x155da78b788ab54bea1340c10a5422a8ae88142f.WorkerName --4g-alloc-size 4080 --zombie-tune 15.25


## Basic miner information


There are three things lolMiner needs in any case to know to start mining, namely
- the algorithm to mine
- the pool or solo node address to connect to
- the user / wallet name to mine for

### Configure the algorithm to mine

There are two ways in lolMiner how to specify the algorithm you want to mine. You need to choose **one** of them to start mining.
 
The first option is **--algo (-a)** followed by one of the following algorithm names
Parameter | Algorithm 
| ------------- | ------------- |
| AUTOLYKOS2 | Autolykos V2  |         
| BEAM-I | BeamHash I  |
| BEAM-II | BeamHash II  |
| BEAM-III | BeamHash III |
| C29D  | CuckarooD 29  |
| C29Z | CuckarooZ 29 |
| C30CTX | Cuckaroo 30 Cortex |
| C31 | Cuckatoo 31   |
| C32 | Cuckatoo 32   |
| EQUI144_5 | Equihash 144/5  |                  
| EQUI192_7 | Equihash 192/7  |                  
| EQUI210_9 | Equihash 210/9  |                  
| ZEL | ZelHash |

Note that you always can call `lolMiner --list-algos` to get a list of all supported algorithms as well as the fee height. Also the list will inform you if the algorithms supports / requires the personalization option **(--pers)** that is required for some of the Equihash algorithms. 


The 2nd way to configure lolMiner is via the parameter **--coin (-c)**. This parameter does set more detailed settings for selected profiles and allows special functions, e.g. algorithm switchers or combination of an algorithm with the right personalization. 

Available entries for --coin are:

Parameter | Description 
| ------------- | ------------- |   
| AION | Selecting Equihash 210/9 and right settings to mine Aion |
| AUTO144_5 | Mine Equihash 144/5 and allow the pool to select the personalization |    
| AUTO192_7 | Mine Equihash 192/7 and allow the pool to select the personalization |    
| BEAM | Mine Beam and switch algorithm on Beam Hash II / III fork height |    
| BTCZ | Mine Equihash 144/5 with personalization for BitcoinZ  |  
| BTG  | Mine Equihash 144/5 with personalization for Bitcoin Gold  |
CTXC | Select settings & stratum to mine Cortex Ai |
EXCC | Select settings & stratum to mine Exchange Coin |
GRIN-C29M | Select settings & stratum to mine Grin C29 |
GRIN-C32  | Select settings & stratum to mine Grin C32 |
MWC-C29D  | Select settings & stratum to mine MWC C29 |
MWC-C31  | Select settings & stratum to mine MWC C31 |     
XSG | Mine Equihash 144/5 with personalization for Snow Gem |    
YEC | Mine Equihash 192/7 with personalization for YCash |
ZCL | Mine Equihash 192/7 with personalization for Zclassic |
ZER  | Mine Equihash 192/7 with personalization for Zero |

Note that you always can call `lolMiner --list-coins` to get a list of all supported coin configurations as well as the fee height.

### Give the pool address, port and user name / wallet to mine on.

The parameter to select the mining pool to connect to is given by **--pool**. Note that this option takes the address as well as the port in the format `<pool address>:<pool port>`.

The user name or wallet will be passed with the parameter **--user**. In case you pool requires a password to log in you can add the optional parameter **--pass**.

**To configure fail-over pools** the options --pool --user and --pass can be passed multiple times to the miner. They will be processed in order, so the first occurrence belongs to the primary connection, the second to the first fail-over and so on. When the miner looses connection to the primary pool too often (5 times in a short period of time), it will try to connect with the second set of credentials.  

## One line examples

Start to mine Beam automatic Beam Hash II / III switcher on sunpool

`lolMiner --coin BEAM --pool beam.sunpool.top:3334 --user 32f2e8765c2e8f5ea41becc5f397024c94d80cc5fc50ee917af23b260ecb3a5f.workerName` 


Start to mine Grin-C32 on 2Miners pool

`lolMiner -a C32 --pool asia-grin.2miners.com:3030 --user 2aHR0cHM6Ly9ncmluLmJpdG1lc2guY29tL3d1Q3BLeW5kVllZanFQQm1ldHRCNWJjMjE2.workerName` 

or

`lolMiner --coin GRIN-C32 --pool asia-grin.2miners.com:3030 --user 2aHR0cHM6Ly9ncmluLmJpdG1lc2guY29tL3d1Q3BLeW5kVllZanFQQm1ldHRCNWJjMjE2.workerName` 


Start mining BeamHash I with personalization for DEFIs on sunpool:

`lolMiner -a BEAM-I --pers GrimmPOW --pool defis.sunpool.top:3334 --user 32f2e8765c2e8f5ea41becc5f397024c94d80cc5fc50ee917af23b260ecb3a5f.workerName`
