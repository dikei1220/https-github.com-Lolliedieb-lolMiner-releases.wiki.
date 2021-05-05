The "wall of stats". To personalize your stats there are different parameters, you only need to select what you want to show. You have to add _--statsformat_ and values separeted by comma:

* gpuName : A shortcut name of the GPU, e.g. "RX 580" or "RTX 2060"
* algo : The current algorithm running. Only visible in dual modes
* speed : Speed in Mhs of the rig
* inflatedHr : Inflated Speed Mhs to compare it to the stats of inflated miners
* poolHr: Pool Average, it will say how luck or unluck are you. If it is higher than the speed that means you are lucky if it is lower you are in an unlucky moment. That will take in long time to the same as speed.
* shares: Number of shares submited. A: parameter is shares, S: are Stales and Hw: are Hardware errors
* sharesPerMin : Number of shares accepted per minute
* bestShare: Best share you have
* power: Power Consumption, normally in Nvidia is quite real to the Wall Watts and AMD is different depending on the board
* hrPerWatt: Efficiency of Mhs you get for 1 Watts usage
* wattPerHr: Efficiency of the Watts you need to have 1 Mhs
* coreclk: Core Clock in Mhz 
* memclk: Memory Clock in Mhz, that depending on Nvidia or AMD it is show different
* coreT: Temperature of the Core
* juncT: Temperature Junction of the Core, this will be avalaible in all Polaris & newer
* memT: Memory Temperature, this is not avalaible in all the GPUs, at the moment only in Vega, Navi and Big Navi
* fanPct : Fan speed in %
* speedctxc : Does the g/s to h/s conversion for cortex (CTCX)
* fidelity : Cuckoo Solver Accuracy, fraction of found graph cycles over expected number



For example, that will show nearly all information:
_--statsformat speed,poolHr,shares,sharesPerMin,bestShare,power,hrPerWatt,wattPerHr,coreclk,memclk,coreT,juncT,memT,fanPct_
![All Stats](https://i.ibb.co/g3q5R0X/allstats.jpg)


For example, that will show Speed, Pool Hr, Shares, Shares Per Minute, Hr Per Watts and Watt Per Hr :
_--statsformat speed,poolHr,shares,sharesPerMin,hrPerWatt,wattPerHr_

![Partial Stats](https://i.ibb.co/zH5bjGB/parcialstats.jpg)

For example, that will show Speed, Inflated Speed, Pool Hr, Shares, Shares Per Minute, Best Share, Hr Per Watts and Watt Per Hr, Core Clock, Mem Clock, Core Temp, Core Junction Temp, Memory Temp and Fan Percentage :
_-statsformat speed,inflatedHr,poolHr,shares,sharesPerMin,bestShare,power,hrPerWatt,wattPerHr,coreclk,memclk,coreT,juncT,memT,fanPct_

![Inflated Stats](https://i.ibb.co/6tmKgVH/inflated.jpg)