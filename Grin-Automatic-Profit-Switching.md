## Introduction

Mining Grin is not straight forward as there are currently three relevant proof of works on the chain, namely C29M, C31 and C32. Each of the proof of works get differently high rewards that may change with every new block adjusting the scale factors between C29M and C31 / C32. The same time slowly the consensus increases the C32 profitability over C31. 

Thus the proof of work that is best to mine changes frequently. In order to ease the user experience and to maximize the profitability lolMiner 0.9.7 introduces an auto-switcher between the three algorithms, that determines the best algorithm for your rig based on the speed of its speed and the current active reward scaling factors. 

To use the new feature you will require a pool that allows to mine the different proof of work schemes on the same port. Below you can find a list of pools that were tested with the last release. Note that some pools will need a reconnect when switching the algorithms. For this case the parameter is mentioned in the supported pools list.

There are two methods to run the auto switching function.

## Usage with Automatic Benchmarks

To run the miner with an automatic benchmark of the algorithms you need to start the miner by using

`lolMiner.exe --coin GRIN-AUTO --autobench 1 --pool <yourPool>:<poolPort> --user <yourUserdata>`

In this case the miner will run each of the three algorithms for at least 80 seconds (until the next job from pool arrives after 80 seconds have passed) and determine its performance during this period. Afterwards it will show the estimated performances and switch to the most profitable among the three algorithms.

## Usage without Automatic Benchmarks

If the performances of the algorithms are known or for a more advanced setup you can start the miner with the following parameters 

`lolMiner.exe --coin GRIN-AUTO --c29speed <C29M performance> --c31speed <C31 performance> --c32speed <C32 performance> --pool <yourPool>:<poolPort> --user <yourUserdata>`

In this case the miner will not run a benchmark and instead use the values given by the user. Then the miner will switch to the most profitable algorithm according to the given numbers. 

This mode has advantages and disadvantages over the automatic benchmark. On the advantage side is, that one of the algorithms can be deactivated by picking 0 as speed entry. Also the user can lower a value slightly in case that a different energy consumption is recognized and he wants to account for this. On the contra side the miner does not correct wrong values given by the user, so please double check before starting the miner.

## List of Supported Pools

| Pool    |   Algorithms |      Options Required
--- | --- | ---
|2Miners  |      All     |  --reconnectOnSwitch 1
|btc.com  |  C29M & C31 (1) |           none
|F2 Pool  |  C29M & C31 (2) |           none
|Grinmint |      All     |           none

(1) C32 shares are accepted and listed as C31 ones

(2) C32 shares are accepted but not yet credited

Note about the reconnectOnSwitch option: Some pools may require this switch because else the first submitted shares after a switch may get rejected. In this case the total switch time is approx 3 seconds instead of some milliseconds. During normal operation the miner only should switch few times a day, such that the reconnect is no issue, but during the benchmark phase the pool will in total reconnect four times. 

All pools above were checked if they require this option, in case its needed its mentioned in the table above. 