The "wall of stats". To personalize your stats there are different parameters, you only need to select what you want to show:
* speed : Speed in Mhs of the rig
* poolHr: Pool Average, it will say how luck or unluck are you. If it is higher than the speed that means you are lucky if it is lower you are in an unlucky moment. That will take in long time to the same as speed.
* shares: Number of shares submited. A: parameter is shares, S: are Stales and Hw: are Hardware errors
* sharesPerMin : Number of shares per minute
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


For example, that will show all information:
--statsformat speed,poolHr,shares,sharesPerMin,bestShare,power,hrPerWatt,wattPerHr,coreclk,memclk,coreT,juncT,memT,fanPct
![All Stats](https://i.ibb.co/g3q5R0X/allstats.jpg)


For example, that will show all information:
--statsformat speed,poolHr,shares,sharesPerMin,hrPerWatt,wattPerHr
![Partial Stats](https://i.ibb.co/zH5bjGB/parcialstats.jpg)