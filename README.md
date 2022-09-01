# Powernine BMS
![Overview_Photo.jpg](/img/Overview_Photo_D.png)


This repository is dedicated to the documentation of the Powernine BMS project by SurgeSPB. 
 
 
The repository is split in two parts:
1. **[Hardware](Hardware)**
	The BMS is now out for a quite a long time, so multiple revisions exist. In this folder there are informations on individual parameters and differences of the different revisions and their parameters.
	It also contains information on what FW-versions are available
	**Never flash firmware other than noted**
2. **[Software](Software)**
	All existing BMS support configuration and firmware updating via bluetooth.
	The folder contains:
	  + The configuration tool used for the BMS, PowerNine
	  + Documentation on options available in Powernine, and how to use them
	  + Available firmwares to be used for different BMS revisions
 
	  
## Features

_Current bms revision is **D**_.

|Parameter|Value|
| :--- |---:|
|Physical dimensions|65x35 mm|
|Peak discharge current|60 A|
|Max charge current|6 A|
|Cell balance current| 35 mA|
|Sections balanced at the same time | max 3|
|Balancing algorithm type|passive, 24/7 if no load is detected

This is a custom BMS, based on the stm G031 series. 
Its main feature is the **full support of the Ninebot/Xiaomi communication protocol**. 
It has a very small formfactor, and can deliver up to 60A peak current.
It's highly configurable, and can be configured according to the specific user scenario.
It is also possible to use it in stand-alone mode should you decide to ditch the ninebot ecosystem. 

## Where to buy

If you live in the eastern hemisphere, reach out directly to [Surge](https://t.me/SurgeSPB). 
If you live in Europe, reach out to [AK](https://t.me/aka13).

Please understand, that with current logistical limitations availability is limited and stock goes very quickly. 

## [Quick Setup](/Software/quick_setup.md)
There is a short manual on how to connect and setup the BMS, if you don't want to read the full documentation [here](/Software/quick_setup.md).


## Issues and questions

If you think something is missing/should be fixed in the documentation, or have suggestions, open an issue on github.

If you understand russian, want to discuss stuff, or get tips on the installation, you can join the [official group](https://t.me/ninebotfun). 
If you speak german or english, you can join the european group (coming soon).

## Disclaimer
Please remember, li-ion battaries are no joke. You should have an understanding on what you are doing, and why you are doing it. No BMS in the world is going to save you, if you don't know what you are doing.

Ride safe and obey local laws.