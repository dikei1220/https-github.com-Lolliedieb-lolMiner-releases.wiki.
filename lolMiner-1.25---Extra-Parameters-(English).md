## Extra parameters (Dual Mining, Worker, Zombie-Mode, Dual Kernel CUDA, ...)

**--worker arg** arg will allow you to specify worker name of your rig.
**--devices arg** arg has to be devices number separated by commas like _--devices 0,1,3,4_ will select GPU 0,1,3,4 and skip 2

**--dualmode arg** arg = `zil` or `etc`. Dual mode used. Allowed options: 

**--dualmode zil** will mine ETH or ETC with ZIL. it is recommened to add  the parameter **--enablezilcache**, to enable ZIL cache for a fast swap, between ETH/ETC and ZIL. Examples :

* Shardpool.io: `lolMiner --algo ETHASH --pool eu1-zil.shardpool.io:3333 --user 0x155da78b788ab54bea1340c10a5422a8ae88142f.workerName --pass zil12kfcrls87pzqnneratejhk8xa3wdzlhrdl7w5g@eth.2miners.com:2020@ --enablezilcache --dualmode zil --dualstratum 0x155da78b788ab54bea1340c10a5422a8ae88142f@eth.2miners.com:2020`

* rustpool.xyz:`lolMiner --algo ETHASH --pool eu-zil.rustpool.xyz:8008 --user 0x155da78b788ab54bea1340c10a5422a8ae88142f --pass 0x155da78b788ab54bea1340c10a5422a8ae88142f@eth.2miners.com:2020@4G --worker workerName --enablezilcache --dualmode zil --dualstratum 0x155da78b788ab54bea1340c10a5422a8ae88142f@eth.2miners.com:2020`

* k1pool.com: `lolMiner --algo ETHASH --pool eu.ethash.k1pool.com:5000 --user K1LOGIN.workerName --enablezilcache --dualmode zil --dualstratum 0x155da78b788ab54bea1340c10a5422a8ae88142f@eth.2miners.com:2020`

* ezil.me: `lolMiner --algo ETHASH --pool eu.ezil.me:5555 --user 0x155da78b788ab54bea1340c10a5422a8ae88142f.zil12kfcrls87pzqnneratejhk8xa3wdzlhrdl7w5g --worker workerName --enablezilcache --dualmode zil --dualstratum 0x155da78b788ab54bea1340c10a5422a8ae88142f@eth.2miners.com:2020`

**--dualmode etc** will mine Mine ETH on 8G cards while mining ETC on 4G cards. Examples :`lolMiner --algo ETHASH --pool eth.2miners.com:2020 --user 0x155da78b788ab54bea1340c10a5422a8ae88142f --dualmode etc --dualstratum 0x155da78b788ab54bea1340c10a5422a8ae88142f@etc.2miners.com:1010`

**--ethstratum arg** arg = `ETHPROXY` or `ETHV1`, this  Ethash stratum mode. Available options: `ETHPROXY`: Ethereum Proxy and `ETHV1`: EthereumStratum/1.0.0 (Nicehash), when you are mining in dual mode, you can select `--ethstratum ETHPROXY,ETHV1`, that will make that the 2nd connection the ETH or ETC will use the Nicehash connection. Useful to mine dual mining ETH + ZIL when the ETH pool is Nicehash.

**--4g-alloc-size arg** arg sets the DAG size (in MByte) the miner is allowed to use on 4G cards. Can be a comma separated list of values for each card. Suggested values in Linux: 4080, 4078, 4076, 4074, 4072, 4070, 4068, 4064, 4062. The higher value the most performance.

**--zombie-tune arg**  arg sets the Zombie tune mode, it can be `auto` or values from `0-16`. When Zombie Mode is run it will inform after the auto tune, which is the optimal values, so it can be used as a parameter next time, avoiding the autotune time. Example:

* First time run, with --4g-alloc-size 4080. 
`lolMiner --algo ETHASH --pool eth.2miners.com:2020 --user 0x155da78b788ab54bea1340c10a5422a8ae88142f.WorkerName --4g-alloc-size 4080 --zombie-tune auto`

* When you have the Zombie-tune Value and --4g-alloc-size 4080 :
`lolMiner --algo ETHASH --pool eth.2miners.com:2020 --user 0x155da78b788ab54bea1340c10a5422a8ae88142f.WorkerName --4g-alloc-size 4080 --zombie-tune 15.25`

**--mode arg** arg can be `a` or `b`. `b` is by default, a low Watts kernel for mining with Nvidia with CUDA. It can have comma separated values for configuring multiple cards differently. mode `a` maximize Mhs and mode `b` has fewer Mhs but with an import improve in Watts. This particular mode has to be used in combination with Fix Clock. AMD Cards should be `a`. Example:

`lolMiner --algo ETHASH --pool eth.2miners.com:2020 --user 0x155da78b788ab54bea1340c10a5422a8ae88142f.WorkerName --mode a,b,b,a,a`

That will select for GPU 0,3,4 the Kernel Mode `a` and GPU 1,2 will be `b`.