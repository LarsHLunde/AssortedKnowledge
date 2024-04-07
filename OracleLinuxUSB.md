#How to create a bootable Oracle Linux install drive
## Pre-requisites
For this guide, you will need  
- 16GB USB stick
- Windows computer
- Rufus installed from https://rufus.ie/en/
- Oracle Linux ISO downloaded from https://yum.oracle.com/oracle-linux-isos.html  
  (make sure to get the FULL iso)

## Creating the bootable USB
Open Rufus  
1. Make sure you have the correct USB drive selected  
2. Click select and locate your ISO  
3. Once selected, make sure it says MBR  
![image](https://github.com/LarsHLunde/AssortedKnowledge/assets/5747758/7dc63ac1-0a3e-4bef-98c5-ca9d43f9cdf2)

Once all settings are in, click start,  
there may come a warning, just click ok.  

### Write in ISO mode!  
![image](https://github.com/LarsHLunde/AssortedKnowledge/assets/5747758/acbd2a98-2870-470f-950c-a17d783751fc)


Tested with vmware and plopkexex:  
https://www.plop.at/en/plopkexec/full.html  
and on real hardware.  
  
- ODA baremetal OS ISO 19.22 (p30403643)  
- Oracle Linux 7.9
- Oracle Linux 8.8
