# 16S BMS Revision C


![16s_RevC.png](/img/Hardware/16s_RevC_schematic.png)

**Latest firmware is 711.**
Download it from the filelist above.
Firmware flashing is done with XIAOFLASHER.

## Connections 
1. Balancer connector
2. Battery connection
3. Load connection (to the ESC)
4. To charger
5. Data connection to the ESC
6. Thermistors 

The BMS comes **pre-wired** for the stock ninebot DC charger connector. The **stock connector to the charger port MELTS when charging over 4,5A**. If you plan charging with higher currents, change the connector.

Please consider the fact, that when running 60A through the BMS, the discharge mosfets dissipate about 4W of heat, which needs to be moved away from the BMS. Attach a heatsink from the bms to the frame to prevent failure through mosfet overheating. 

## Parameters

This revision has the following parameters:
|Parameter|Value|
| :--- |---:|
|Physical dimensions|65x35 mm|
|Peak discharge current|60 A|
|Max charge current|6 A|
|Cell balance current| 55 mA|
|Sections balanced at the same time | max 3|
|Balancing algorithm type|passive, 24/7 if no load is detected

## Connecting

1. Attach power and charge wiring of desired length to the BMS. If needed, replace the charging connector.
2. Place the BMS in a printed holder, or attack it securely to the battery. Make sure that no part of the BMS touches metal. You can use one of the available holders from [here](/stl).
3. Attach balancing wires in correct order. 
**You MUST start with the B0** Or the negative load cable. After you have connected the B4 cable, the bms will be on and in the configuration mode, indicated by blinking of the red and green LEDs in sequence. Ignore the LEDs until the B4 is connected.
4. After connecting the remaining wires (**B16 or positive load cable MUST be last**) the BMS will automatically exit the setup mode and start blinking with the green LED. If it is not blinking, then you made a mistake while connecting the cables, and the sections were not recognized. You need to repeat the connection process.
5. If connecting less than 16 sections, you start with the B0, and connect the sections until the the second to last one. The unused wire are connected together on the BMS, and the last section is connected to B16. See the picture below for better understanding.

![16s_RevC_balancer.png](/img/Hardware/16s_RevC_balancer.png)

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
