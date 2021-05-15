**Lolminer is not recognized as external or internal command**
> That problem appears when the lolMiner.exe it is not in the same folder of the bat file. That normally happens when you try to run as administrator the bat file or when the Windows Defender or Antivirus has deleted the lolMiner.exe. In this last case, please you should need to disable the Windows Defender or Antivirus or exclude the folder of the lolMiner

**OC crashes**
> Normally a GPU crashes is for an extreme overclock or undervolt... It is interesting in case that happens post the error with photo and the OC in the issues.


**iGPU will not mine"**
> Any integrated GPU will NOT work with lolMiner. All integrated GPU like Intel HD620, 630, Vega 3, Vega 8, 10, ... will not work with lolMiner. lolMiner need dedicated GPU to work.

**Old Cards**
> Any Nvidia GPU before Fermi/Kepler/Maxwell will not work like GTX 770.

**4Gb Card Windows ETH**
> It is not possible to mine any more in Windows with 4Gb cards, the only option for this 4Gb are to use Linux. Also, it will only work in Linux with AMD 4Gb cards in Zombie Mode. The solution in Windows for 4Gb or less it is to mine other algos, like ETC, ZEL, ...

**Nvidia Problems Windows Half Rate**
> That was an old problem solved with version 1.25 and more, with the introduction of CUDA mining. Please update to a newer version to avoid that problem when adding more than 2 GPU.

**Loop Solution for crash**
> When the driver crashes it is useful to have a loop solution in the bat file. That automatically after 10 seconds it restarts the miner. After 1.29 the loop solution is applied in all algorithms. Please try to be updated. 

**Strange Characters in console**
> That usually come to try to show the console with colours, if that happens you only need to add parameter --nocolor in the config lane. That will let you to see it without that characters.

**Zombie Mode and Nvidia**
> It is not possible to mine any more in Windows or Linux with Nvidia 4Gb cards. Zombie mode only works in Linux for AMD 4Gb cards. The solution for the Nvidia 4Gb cards or less is to mine other algos, like ETC, ZEL, ...
