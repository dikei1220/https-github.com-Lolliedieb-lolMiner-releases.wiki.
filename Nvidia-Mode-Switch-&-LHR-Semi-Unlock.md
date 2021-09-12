# --mode switch on Nvidia GPUs (also for LHR control)
--mode controls the loaded kernel and operation modes for Nvidia GPUs. AMD cards will currently ignore this parameter completely. You can set one value for the whole rig or provide a comma separated list of values to get individual modes for each card. Amd cards can use any value at the moment. 

## --mode a
This is the often fastest kernel when you do not apply any power limit. Gives better performance especially on RTX 3080 and 3090, but not so much on the lower tier GPUs. Use this one when power draw does not matter any ways.

## --mode b (default)
This is a power saving kernel an the default. Good choice for all Non-LHR Nvidia GPUs and RTX 3060 LHR V1 on the known 470.05 beta Windows driver. Also this mode will be used in glitch mode.

## --mode LHR1
This is the default mode for RTX 3060 LHR v1 when the driver version is between **455.45.01** and **460.39**. Gives up to 80% of the potential unlocked raw card performance. In case other driver versions get used, the miner falls back to the LHR2 mode.

## --mode LHR2
This mode is made for all other LHR (v2) Nvidia RTX 3000 cards. Performance is approximately 67-69% of the potential unlocked raw card performance. Note that the mode was tested with a locked core clock of 1500 mhz on all cards. Higher core clock may work, but could also cause the lock to trigger on your card, especially when the card is only power limit bound and has no fixed upper core bound!

## --mode LHRLP

This mode can be used, when the core clock of the GPUs is **locked** below the values listed in the table.

| GPU        |  3060  | 3060 Ti | 3070 | 3070 Ti | 3080 | 3080 Ti |
| ------------- |---------:|---------:|---------:|---------:| ---------:|---------:|  
| Max core | 1150 Mhz | 1150 Mhz | 855 Mhz | 855 Mhz | 1050 Mhz | 1150 Mhz |

With this low clocks the performance is generally lower, but the LHR semi-unlock parameters can get relaxed to give a higher share of the potential the GPU has. Therefore unless you run much higher core it often can be a good idea to lower the core clock to the limits stated above.
Note: This is **recommended mode** for all **3080** and **3080ti**!

## Tuning
The values we have chosen as parameters were taken after elaborate tests. Sadly the best config changed from rig to rig, so there is a parameter --lhrtune that takes a comma separated list of values. Negatives will relax settings, so the GPU will more likely unlock, positives will make the lock more likely, but improve performance. 

If you have a card not starting unlocked, try a value of -20 as a start, lower might be needed. This is true especially when you have your card in motherboard x16 slot.  If your cards are super stable try to increase in small steps of 5. 

## Fan glitch mode
For all LHR GPUs that were started with one of the LHR modes and the fan glitch gets detected, the card will leave the LHR mode to unlock the full performance of the card. In most situations the appearance of the glitch triggers a one time card crash that makes the mining OS restart the mining software. The glitch detection allows to mine in LHR mode until a glitch on one card appears. On the next restart of the software the glitches cards will then mine with LHR mode disabled while the remaining cards keep on mining in their configuration. 

## Examples
_--mode LHR2 --lhrtune 10,5,-15,15,15,15_ that will apply all the rig mode LHR2 and to GPU0 tune 10, GPU1 tune 5, GPU2 tune -15, and GPU 3/4/5 tune 15

_--mode b,b,b,LHRLP,b,b,b,b --lhrtune -3_ that will apply mode b to all rig except to GPU3 that will use mode LHRLP, the tune value will only affect the LHR Kernel, in this case the LHRLP with a tune value of -3.