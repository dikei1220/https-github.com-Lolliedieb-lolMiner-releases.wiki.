To fix the clock Power Limit, doesn't need to be fixed. If you specify a Power Limit and is too low, the clock will not get fixed. So It is a good recomendation to put a high Power Limit and reduce the Watts with the Fix Clock Solution, only for Turing and Ampere.

_Linux:_

**HiveOS:** You have to put the direct value in the +Core Clock Mhz, in this example we are putting 750Mhz to the RTX 3070, only avaliable after 0.6-202@210331.

<a href="https://ibb.co/4SnJJxs"><img src="https://i.ibb.co/YdFbbGD/HiveOS.jpg" alt="HiveOS" border="0"></a>

**MMPOS:** In Settings you have to select 'Lock GPU clock frequency`, in this example we are putting 750Mhz to the RTX 3070

<a href="https://ibb.co/2ybwzMv"><img src="https://i.ibb.co/s2BhT1K/MMPOS.jpg" alt="MMPOS" border="0"></a>

**RaveOS:** In Set you have to specify this parameter: `oc --fixclk=value`, , in this example we are putting 765Mhz to the RTX 3070

<a href="https://ibb.co/zFBSNQP"><img src="https://i.ibb.co/m02HSbh/RaveOS.jpg" alt="RaveOS" border="0"></a>

_Windows 10:_

**Msi Afterburner:**
1. You can set a flat V/F curve using MSI Afterburner.
1. Drag your core clock slider all the way to the left.
1. Hit apply.
1. Ctrl + F to open the V/F curve.
1. Find the voltage you want to run and drag it up to the frequency you want to run.
1. Hit apply and everything to the right of your selected point should flatten out.

CTRL + F: open the voltage curve menu

CTRL + L: lock voltage and frequency to the highlighted dot

Tab / Shift-Tab: select next/previous dot

CTRL + UP / CTRL + DOWN: increase/decrease the frequency of the selected dot by 10 (it would be 1 without ctrl)

**Manually**: That will work for _Linux_ and _Windows 10_ `nvidia-smi -i $GPU -lgc $VALUE`

Values: 
| GPU        | Range       | 
| ------------- |:-------------:| 
| 2070 | 1000 - 1050 |
| 2080 | 1110 - 1160 |
| 3060 (1) | 1070 - 1120 |
| 3060ti | 1320 - 1370 |
| 3070 | 750 - 800 |
| 3080 | 1010 - 1060 |

(1) Windows with 470.05 Drivers