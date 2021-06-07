## Using the dual & splitting modes

### Use case A: Mine ZIL&ETH or ZIL&ETC on different pools

Usually when mining ZIL you need to mine ETH on the same pool or you need to rely on a pool proxy forwarding mechanism implemented by the pool. The first case restricts restricts your mining to a single pool while the latter might have the disadvantage of a worse ETH mining latency or pool forwarding instabilities. lolMiner 1.20 and up allow to bypass the situation by adding a second stratum connection that will pick up your ETH (or ETC) shares and bring them directly to the pool you like, while the ZIL shares will be send during the ZIL shard epochs to the ZIL pool.  

To configure this follow the following steps

* a) Configure your ZIL mining as normal. In case you want to use ETC+ZIL select ETCHASH as algorithm parameter. The configuration needs to be complete, that means if you stop after this point you should use normal ZIL+ETH or ZIL+ETC dual mining as you are used to.
* b) Add the parameter --dualmode zil --dualstratum *ETHWALLET*.*ETHWORKER*@*ETHPOOL*:*ETHPORT* to your command line arguments or your extra user parameters. Replace here the elements in *ETHWALLET*, *ETHWORKER*, *ETHPOOL* and *ETHPORT* with your desired ETH mining credentials. Note that <ETHSTRATUM> understands prefixes like "tls://" to activate ssl on the additional stratum connection.

Now the miner will create both connections on startup, but will mine the ETH (or ETC) shares on the extra connection, which can be different to the first one, which will only be used when mining ZIL. Note that the parameter will automatically enabling the ZIL cache mode on your 6 & 8G cards. 

Examples for each pool:

* Shardpool.io: `lolMiner --algo ETHASH --pool eu1-zil.shardpool.io:3333 --user 0x155da78b788ab54bea1340c10a5422a8ae88142f.workerName --pass zil12kfcrls87pzqnneratejhk8xa3wdzlhrdl7w5g@eth.2miners.com:2020@ --enablezilcache --dualmode zil --dualstratum 0x155da78b788ab54bea1340c10a5422a8ae88142f@eth.2miners.com:2020`

* rustpool.xyz:`lolMiner --algo ETHASH --pool eu-zil.rustpool.xyz:8008 --user 0x155da78b788ab54bea1340c10a5422a8ae88142f --pass 0x155da78b788ab54bea1340c10a5422a8ae88142f@eth.2miners.com:2020@4G --worker workerName --enablezilcache --dualmode zil --dualstratum 0x155da78b788ab54bea1340c10a5422a8ae88142f@eth.2miners.com:2020`

* k1pool.com: `lolMiner --algo ETHASH --pool eu.ethash.k1pool.com:5000 --user K1LOGIN.workerName --enablezilcache --dualmode zil --dualstratum 0x155da78b788ab54bea1340c10a5422a8ae88142f@eth.2miners.com:2020`

* ezil.me: `lolMiner --algo ETHASH --pool eu.ezil.me:5555 --user 0x155da78b788ab54bea1340c10a5422a8ae88142f.zil12kfcrls87pzqnneratejhk8xa3wdzlhrdl7w5g --worker workerName --enablezilcache --dualmode zil --dualstratum 0x155da78b788ab54bea1340c10a5422a8ae88142f@eth.2miners.com:2020`

### Use case B: Mine ETH on 8G cards while mining ETC on 4G cards

Usually miners allow using only one algorithm at a time. With lolMiner 1.20 the miner starts supporting to create two connections to your favorite pools and mine two algorithms within the same miner instance. Concretely this mode was build to mine ETCHASH on some GPUS while others stay on ETH. 

To configure this follow the following steps:

 * a) Configure your ETH mining as normal, no further settings are required.
 * b) Add the parameters --dualmode etc --dualstratum *ETCWALLET*.*ETCWORKER*@*ETCPOOL*:*ETCPORT* to your command line arguments or your extra user parameters. Replace here the elements in *ETCWALLET*, *ETCWORKER*, *ETCPOOL* and *ETCPORT* with your desired ETC mining credentials. Note that <ETCSTRATUM> understands prefixes like "tls://" to activate ssl on the additional stratum connection.
 * c) (Optionally) You can use --dualdevices to select those devices that shall mine ETC instead of ETH. The default is that all 3G and 4G cards will be pointed to the secondary algorithm, while the other cards remain on the primary one. The parameter takes a comma separated list of numbers, which needs to be a subset of the devices running. For example the combination of --devices 0,1,2,4,5 --dualdevices 4,5 will cause Cards 0,1 and 2 to mine the first algorithm, cards 4 and 5 the second algorithm and card 3 to be skipped from mining. 

### Use case C: Mine ETH/ETC two different pools

Usually miners allow using only mining at one pool at time. With lolMiner 1.25 the miner starts supporting to create two connections to your favorite pools and mine ETH/ETC within the same miner instance. Concretely this mode was build to mine to share RIGS. 

To configure this follow the following steps:

 * a) Configure your ETH/ETC mining as normal, no further settings are required.
 * b1) Add the parameters for ETH: --dualmode eth --dualstratum *ETHWALLET*.*ETHWORKER*@*ETHPOOL*:*ETHPORT* to your command line arguments or your extra user parameters. Replace here the elements in *ETHWALLET*, *ETHWORKER*, *ETHPOOL* and *ETHPORT* with your desired ETH mining credentials. Note that <ETHSTRATUM> understands prefixes like "tls://" to activate ssl on the additional stratum connection.
 * b2) Add the parameters for ETC: --dualmode etc --dualstratum *ETCWALLET*.*ETCWORKER*@*ETCPOOL*:*ETCPORT* to your command line arguments or your extra user parameters. Replace here the elements in *ETCWALLET*, *ETCWORKER*, *ETCPOOL* and *ETCPORT* with your desired ETC mining credentials. Note that <ETCSTRATUM> understands prefixes like "tls://" to activate ssl on the additional stratum connection.
 * c) You have now to select which devices to use in each connection, with --dualdevices you will select with GPU mine in the 2nd pool, while the other cards remain on the primary one. The parameter takes a comma separated list of numbers, which needs to be a subset of the devices running. For example the combination of --devices 0,1,2,4,5 --dualdevices 4,5 will cause Cards 0,1 and 2 to mine in first pool, cards 4 and 5 the 2nd pool and card 3 to be skipped from mining. 
