## Introduction

Mining Grin is not straight forward as there are currently three relevant proof of works on the chain, namely C29M, C31 and C32. Each of the proof of works get differently high rewards that may change with every new block adjusting the scale factors between C29M and C31 / C32. The same time slowly the consensus increases the C32 profitability over C31. 

Thus the proof of work that is best to mine changes frequently. In order to ease the user experience and to maximize the profitability lolMiner 0.9.7 introduces an auto-switcher between the three algorithms, that determines the best algorithm for your rig based on the speed of its speed and the current active reward scaling factors. 

## List of Supported Pools

| Pool    |   Algorithms |      Options Required
--- | --- | ---
|2Miners  |      All     |  --reconnect-on-switch
|F2 Pool  |   C29M & C31 |           none
|Grinmint |      All     |          none