# 16S BMS Revision C


![16s_RevC.png](/img/Hardware/16s_RevC_schematic.png)

**Latest firmware is 711.**
Firmware flashing is done via XIAOFLASHER.

## Connections 
1. Balancer connector
2. Battery connection
3. Load connection (to the ESC)
4. To charger
5. Data connection to the ESC
6. Thermistors 

The BMS comes **fully pre-wired** with stock ninebot DC charger connector. The **stock connector to the charger port MELTS when charging over 4A**. If you plan charging with higher currents, change the connector.

Please consider the fact, that when running 60A through the BMS, the discharge mosfets dissipate about 4W of heat, which needs to be moved away from the BMS. Attach a heatsink from the bms to the frame to prevent failure through mosfet overheating. 

## Parameters

This revision has the following parameters:
|Parameter|Value|
| :--- |---:|
|Physical dimensions|65x35 mm|
|Peak discharge current|60 A|
|Max charge current|6 A|
|Cell balance current| 35 mA|
|Sections balanced at the same time | max 3|
|Balancing algorithm type|passive, 24/7 if no load is detected

## Connecting

1. Attach bms with holder securely to the battery. Make sure that no part of the BMS touches metal.
2. Attach power ground (thick black wire under B section). 
3. Attach balancing wires in correct order. 
Balancing wires now start from B1.After you have connected the B4 cable, the bms will be on and in the configuration mode, indicated by blinking of the red and green LEDs in sequence. Ignore the LEDs until the B4 is connected.
If connecting less than 16 sections, you start with power ground, and connect the sections until the the second to last one. The unused wire are connected together on the BMS, and the last section is connected to power positive.
**Consult the diagram for you convenience**
4. Attach power positive (thick red wire under B section). The BMS will automatically exit the setup mode and start blinking with the green LED. If it is not blinking, then you made a mistake while connecting the cables, and the sections were not recognized. You need to repeat the connection process.

![16s_RevD_balancer.png](/img/Hardware/16s_RevD_balancer.png)

## Troubleshooting

If you do not have bluetooth access via the BLE/ESC, you can read out some error codes based on the LEDs on the BMS itself. The blinking only happens, when no load is attached to the battery (scooter is turned off)

Following Error Codes are available:

|LED Status|Meaning|
| :--- |---:|
|Red and green blinkinng in sequence| Configuration mode, the BMS waits for sections attechment|
|Red and green constantly on| Firmware update mode. Happens, if the wrong firmware was flashed, or if the flashing was interrupted. Will remain in this mode until firmware is flashed properly. You can also detect this mode by the battery serial number being detected as "UPLOAD MODE" and charge remaining at 5%. BMS can not be configured in this mode.|
|Green flashing quickly, every 2s|Normal standby mode|
|Green flashing slowly| Working mode, load is detected|
|Green on | One or more sections have reached charging cutoff |
|Red on| One or more sections have reached discharge cutoff |
|Red flashing slowly| Charging current detected, battery is charging|
|Red flashing quickly, 2 times| Charging current is too big|
|Red flashing quickly, 3 times| Short circuit or discharge current too high|
|Red flashing quickly, 4 times| Overtemp protection enabled|
|Red flashing quickly, 5 times| Undertemp protection enabled|
