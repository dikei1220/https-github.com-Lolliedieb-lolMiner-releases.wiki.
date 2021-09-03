## Using the dual mode from 1.32

### Mine ZIL&ETH or ZIL&ETC on different pools

Usually when mining ZIL you need to mine ETH on the same pool or you need to rely on a pool proxy forwarding mechanism implemented by the pool. The first case restricts restricts your mining to a single pool while the latter might have the disadvantage of a worse ETH mining latency or pool forwarding instabilities. From lolMiner 1.32 has been improved the bypass the situation by adding a second stratum connection that will pick up your ETH (or ETC) shares and bring them directly to the pool you like, while the ZIL shares will be send during the ZIL shard epochs to the ZIL pool.  

To configure this follow the following steps

* a) Configure your ETH or ETC as normal. In case you want to use ETC+ZIL select ETCHASH as algorithm parameter. 
* b) Add the parameter --dualmode zil --dualpool *pool_of_zil* --dualuser *data_for_the_zil_pool* --dualpass *password_for_the_zil_pool* to your command line arguments or your extra user parameters. Replace here the elements in  *pool_of_zil*, *data_for_the_zil_pool* and *password_for_the_zil_pool* with your desired ZIL mining credentials. 

Now the miner will create both connections on startup, but will mine the ETH (or ETC) shares on the primary connection, and wil mine ZIL in the extra connnection.
 
Note that  to enabling the ZIL cache mode on your 6Gb & 8Gb cards you need to add the parameter _--enablezilcache_ 

Examples for each pool:

* lolMiner --algo ETHASH --pool eth.2miners.com:2020 --user 0x155da78b788ab54bea1340c10a5422a8ae88142f.workerName --enablezilcache --dualmode zil --dualpool eu1-zil.shardpool.io:3333 --dualuser 0x155da78b788ab54bea1340c10a5422a8ae88142f.workerName --dualpass zil12kfcrls87pzqnneratejhk8xa3wdzlhrdl7w5g@eth.2miners.com:2020
* lolMiner --algo ETHASH --pool eu-eth.2miners.com:2020 --user 0x155da78b788ab54bea1340c10a5422a8ae88142f.workerName --enablezilcache --dualpool eu-zil.rustpool.xyz:8008 --dualuser 0x155da78b788ab54bea1340c10a5422a8ae88142f --dualpass zil12kfcrls87pzqnneratejhk8xa3wdzlhrdl7w5g@eth.2miners.com:2020@4G

* lolMiner --algo ETHASH --pool eth.2miners.com:2020 --user 0x155da78b788ab54bea1340c10a5422a8ae88142f.workerName --enablezilcache --dualmode zil --dualpool eu.ethash.k1pool.com:5000 --dualuser KrSv2Z38HuG4fkJBiP4QgYE6osoFfUECmD7

* lolMiner --algo ETHASH --pool eth.2miners.com:2020 --user 0x155da78b788ab54bea1340c10a5422a8ae88142f --enablezilcache -- dualmode zil --dualpool eu.ezil.me:5555 --dualuser 0x155da78b788ab54bea1340c10a5422a8ae88142f.zil1qxl9lwat8rvf3lkn4fluexzh9pwemn0x94nn5a