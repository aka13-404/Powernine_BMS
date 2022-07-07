# Powernine configration manual
This document contains information on the available features, and their usage for the Powernine configuration application. Make sure, that you understand, what and why you change, before any changes. 

---
## 1. Info-Tab
This tab allows you to read currently saved/running parameters of your BMS.
On the top right you see the ESC and the BLE firmware versions.
On the top left you see your e-scooter name and the current mileage.
*If your scooter name is very short, mileage display may be bugged in the current version.*

The main scrollable window contains following fields:
|Field|Value|
|---|---|
|Serial number|The serial number of your ESC|
|Factory capacity|Configured battery capacity|
|Remaining capacity|Calculated remaining capacity of the battery. Remaining charge is multiplied by the configuted factory capacity.
|Accumulated charge| How much energy was pumped into the battery on the last cycle. This is calculated properly based on a colomb meter and numerical integration of the current measurement. |
|Remaining charge| Remaining capacity in %, calculated from the set cell discharge curve and current pack voltage. The average voltage per cell is used for the calculation.|
|Charge count|Increments each time you charge the battery. Counts the number of times when voltage was detected on the charging port.|
|Charge cycles| Increments each time the accumulated charge is > factory capacity, so you can estimate the number of full cycles based on battery capacity.|
|Pack voltage| Pack voltage|
|Current draw| Current draw. Changes sign when charging/discharging.|
|Temperature #1| First battery thermistor. 10K 3930 NTC thermistors are used.|
|Temperature #2| Second battery thermistor. 10K 3930 NTC thermistors are used.|
|Voltage threshold|Max cell voltage difference in V|
|Cell voltage #X| Displays cell segment voltage. Also displays, which cell blocks (if any) are being balanced| 
---
## 2. Config-Tab
This tab allows you to adjust your BMS settings and get additional information.
**The values you set are applied automatically, when the bms goes into sleep mode. This happens after about 3-5 seconds after turning off the load.** The "Apply settings" button is depreciated and will be removed in future versions, does not do anything for the current revision. 
&nbsp;

### 2.1 "General" section
#### 2.1.1. Factory capacity
 You can set the capacity of your battery in mAh. To calculate the capacity, count the number of cells that you have in parallel (for example, 7p) and multiply it with the capacity that the individual cells have (for example, 3000mAh). 7P * 3000mAh = 21000 mAh.
 
#### 2.1.2. Power voltage
An additional debug metric to the pack voltage in the info tab.
*Depreciated, will be removed in future updates*

####  2.1.3. Charge voltage
An estimation of the voltage at the charging port. Useful for debugging issues with charging, and detecting damage to the charging port.

####  2.1.4. Frontend temp
The temperature of the main BMS chip, which is responsible for the heavy lifting when balancing. You may want to reduce the number of balanced cells if this gets too hot for your liking. 

####  2.1.5 Braking voltage
Ninebot escs can  disable the electronic brake, when issued a specific command, to not overload the battery. You can set a voltage (based on individual sections) over which no regenerative breaking is performed to extend the life if your battery.

&nbsp;
### 2.2 "Voltages" section
#### 2.2.1 Cell undervoltage
You can set a voltage (based on individual sections), below which the discharge fets will be disabled. Be careful, when adjusting this parameter, it should be lower, than your %-cutoff in the esc firmware, otherwise you might end up with the scooter suddenly turning off at an unexpected moment.
#### 2.2.2 Delay
You can set a time delay, which has to pass after reaching the trigger value, before undervoltage protection kicks in. Useful against battery sag, so that you don't fall into protection while accelerating at low voltages close to the cutoff.
#### 2.2.3 Recovery
You can set a delta recovery voltage after reaching the trigger value, after which the protection is disabled. Since battery voltage sags under load, this can and should be configured according to the health and sag of your battery. 
&nbsp;
#### 2.2.1 Cell overvoltage
You can set a voltage (based on individual sections), over which the charge fets will be disabled. 4,199 and lower is a safe value for any li-ion cell. 
#### 2.2.2 Delay
You can set a time delay, which has to pass after reaching the trigger value, before the overvoltage protection kicks in. 
#### 2.2.3 Recovery
You can set a delta recovery voltage, after which the protection is disabled. Since the voltage drops slightly after charge, this can and should be configured according to your charger and battery health.
&nbsp;
### 2.3 "Currents" sections
#### 2.3.1 Short circuit
This is the short-circuit protection current  of the BMS. It is recommended to set this current to 5x of your maximum rated current for the battery. Example: If you have cells, which can do 10A per cell, and you have 5 cells in parallel, this would mean 10A*5P*5=250A. 
*The preview in the overview is currently bugged and always displays 80A, no matter what is configured.*
#### 2.3.2 Delay
You can set a time delay, which has to pass, before the short-circuit overcurrent protection kicks in.
#### 2.3.3 Recovery
You can set a minimum time after reaching the trigger value, before the protection is disabled. 
#### 2.3.4 Max charge current
You can limit the charging current, if needed. 8A is the limit for the current revision.
#### 2.3.5 Delay
You can set a time delay, which has to pass after reaching the trigger value, before the overcurrent charging protection kicks in.
&nbsp;
### 2.4 "Temperatures" sections
#### 2.4.1 Overtemp charge
You can set the maximum temperature, over which **charge** FETs are disabled. Most li-ion batteries should not be charged when warmer than 45C. Please set this protection in accordance with your battery. 
#### 2.4.2 Delay
You can set a time delay, which has to pass after reaching the trigger value, before the overtemp protection kicks in.
#### 2.4.3 Recovery
You can set a minimum temperature the battery has to cool down to, before the overtemp protection is disabled. This should be set about 3-5C lower than the 'overtemp charge' parameter to avoid issues.
#### 2.4.4 Overtemp discharge
You can set the maximum temperature, over which **discharge** FETs are disabled. Most li-ion batteries should not be discharged when warmer than 60C. Please set this protection in accordance with your battery. The hotter the battery, the faster it degrades.
#### 2.4.5 Delay
You can set a time delay, which has to pass after reaching the trigger value, before the overtemp protection kicks in.
#### 2.4.6 Recovery
You can set a minimum temperature the battery has to cool down to, before the overtemp protection is disabled. This should be set about 3-5C lower than the 'overtemp charge' parameter to avoid issues.
&nbsp;
#### 2.4.7 Undertemp charge
You can set the minimum temperature, under which **charge** FETs are disabled. Li-ion batteries **can not be charged under 0C**. It causes Lithium plating of contacts and causes significant additional risks towars fires and explosions. 
#### 2.4.8 Delay
You can set a time delay, which has to pass after reaching the trigger value, before the undertemp protection kicks in.
#### 2.4.9 Recovery
You can set a minimum temperature the battery has to reach, before the undertemp protection is disabled. This should be set about 2-3C higher than the 'undertemp charge' parameter to avoid issues.
#### 2.4.10 Undertemp discharge
You can set the minimum temperature, under which **discharge** FETs are disabled. Most Li-ion batteries can not be discharged when under -20C, and **operation under 0C should be avoided**. 
#### 2.4.11 Delay
You can set a time delay, which has to pass after reaching the trigger value, before the undertemp protection kicks in.
#### 2.4.12 Recovery
You can set a minimum temperature the battery has to reach, before the undertemp protection is disabled. This should be set about 2-3C higher than the 'undertemp charge' parameter to avoid issues.
&nbsp;
### "State of charge" section
#### Cell resistance
You need to set the cell resistance for your battery sections, **this is important for battery SoC calculation**, otherwise your SoC will mean nothing and jump around due to voltage drops and not compensating for EMF. Here is how to calculate it: 
1. Measure or estimate your cell ACIR(internal resistance) based on the manufacturers spec. Should be usually <30 mOhm, even if you have reclaimed cells. Cells connected in parallel should have about the same ACIR.
2. Calculate the total resistance of the section by applying Kirchhoffs law for parallel currents. 
Example: You have 6 cells in parallel, they have on average 25mOhm resistance.
25/6=4,1=approx 4 mOhm. 

#### Discharge curve
You can adjust the voltage-discharge curve of your battery. Refer to the manufacturers specs if you want to adjust this. Can be useful for better SoC estimation. 
&nbsp;

### "Balancing" section
#### Min cell voltage
The balancing is passive - this means, cells, which are over the set balancing threshold get discharged, and their energy is "wasted". This means, you may want to limit the voltage, under which no balancing is performed. It is more than sufficient to balance after your normal charging process with voltage over 4.05-4.1, but depending on the age, health and disbalance of the battery, you may want to go lower or higher.

#### Balancing threshold 
You can set a minimal cell difference between sections, below which no balancing is performed. The less voltage difference between cells, the better, but depending on battary age and health you may want to go higher or lower.

#### Cell count
This determines, how many sections can be balanced at the same time. Due to passive balancing, more sections balanced - more heat on the bms. Depending on the heat you see on the bms in 2.1.4 and the season/weather you may want to go up or down with this value. You can balance up to 3 sections at the same time, adjanced sections are not balanced at the same time, to avoid overheating the bms. You can see which sections are getting balanced in the info tab of the app. The bms accounts for voltage sag when balancing.
&nbsp;

### "Blackbox" section
#### Latest overvoltage snapshot
When overvolage protection is triggered, you can check here, what specifically was the cause for the trigger and the cell state at that moment.

#### Latest undervoltage snapshot
When undervoltage protection is triggered, you can check here, what specifically was the cause for the trigger and the cell state at that moment.

#### Connected cells
You can check here, if all sections are connected properly. If you don't see a section here, which is supposed to be there, you have a mechanical connection problem.

#### Check for updates
Depreciated, will be removed in future versions. Does not do anything.