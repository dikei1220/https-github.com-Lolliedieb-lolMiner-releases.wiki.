This page describes to start basic mining until lolMiner 1.25 and newer.

For a detailed list of more lolMiner parameters you can check `lolMiner -h`.

## Basic parameters in command line

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

Note that you always can call `lolMiner --list-algos` to get a list of all supported algorithms as well as the fee height. Also the list will inform you if the algorithms supports / requires the personalization option (--pers) that is required for some of the Equihash algorithms.


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
|ETC | Select settings & stratum to mine Ethereum Classic |
|ETH | Select settings  & stratum to mine Ethereum |
|CTXC | Select settings & stratum to mine Cortex Ai |
|EXCC | Select settings  & stratum to mine Exchange Coin |
|GRIN-C29M | Select settings & stratum to mine Grin C29 |
|GRIN-C32  | Select settings & stratum to mine Grin C32 |
|MWC-C29D  | Select settings & stratum to mine MWC C29 |
|MWC-C31  | Select settings & stratum to mine MWC C31 |
|XSG | Mine Equihash 144/5 with personalization for Snow Gem |
|YEC | Mine Equihash 192/7 with personalization for YCash |
|ZCL | Mine Equihash 192/7 with personalization for Zclassic |
|ZEL | Mine Zelhash & stratum to mine FLUX (ZEL) |
|ZER  | Mine Equihash 192/7 with personalization for Zero |

Note that you always can call `lolMiner --list-coins` to get a list of all supported coin configurations as well as the fee height.

### Give the pool address, port and user name / wallet to mine on.

The parameter to select the mining pool to connect to is given by **--pool**. Note that this option takes the address as well as the port in the format `<pool address>:<pool port>`.

The user name or wallet will be passed with the parameter **--user**. In case you pool requires a password to log in you can add the optional parameter **--pass**.

**To configure fail-over pools** the options --pool --user and --pass can be passed multiple times to the miner. They will be processed in order, so the first occurrence belongs to the primary connection, the second to the first fail-over and so on. When the miner looses connection to the primary pool too often (5 times in a short period of time), it will try to connect with the second set of credentials.


## One line examples

Start to mine ETH on 2miners pool:

`lolMiner --algo ETHASH --pool eth.2miners.com:2020 --user 0x155da78b788ab54bea1340c10a5422a8ae88142f.WorkerName`

Start to mine ETC on 2miners pool:

`lolMiner --algo ETCHASH --pool etc.2miners.com:1010 --user 0x155da78b788ab54bea1340c10a5422a8ae88142f.WorkerName`

Start to mine Beam automatic Beam Hash II / III switcher on sunpool

`lolMiner --coin BEAM --pool beam.sunpool.top:3334 --user 32f2e8765c2e8f5ea41becc5f397024c94d80cc5fc50ee917af23b260ecb3a5f.workerName`

Start to mine Grin-C32 on 2Miners pool

`lolMiner -a C32 --pool asia-grin.2miners.com:3030 --user 2aHR0cHM6Ly9ncmluLmJpdG1lc2guY29tL3d1Q3BLeW5kVllZanFQQm1ldHRCNWJjMjE2.workerName`

or

`lolMiner --coin GRIN-C32 --pool asia-grin.2miners.com:3030 --user 2aHR0cHM6Ly9ncmluLmJpdG1lc2guY29tL3d1Q3BLeW5kVllZanFQQm1ldHRCNWJjMjE2.workerName`

Start mining BeamHash I with personalization for DEFIs on sunpool:

`lolMiner -a BEAM-I --pers GrimmPOW --pool defis.sunpool.top:3334 --user 32f2e8765c2e8f5ea41becc5f397024c94d80cc5fc50ee917af23b260ecb3a5f.workerName`


