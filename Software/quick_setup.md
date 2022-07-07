# Quick setup 

1. Connect your BMS to your battery according to your revisions manual [here](/Hardware/). The revision is noted on the lower right corner of the PCB. Current revision number is [C](/Hardware/16s_RevC.md).
2. Update your firmware. Use xiaoflasher to flash the latest BMS firmware. Firmware can be found in the [software](/Software/) folder.
   1. Open xiaoflash, connect to your scooter
   2. Select the .zip and press flash. Ignore the warnings, that this firmware is for another scooter
   3. Wait for flashing to finish
3. Enter the correct capacity of your battery in the config, [factory capacity option](/Software/README.md#211-factory-capacity) Use the capacity of a cell, multiply it with how many cells you have in parallel. Example: For a 16s5p battery with 3000 mAh cells: 3000mAh * 5P = 15000mAh.
4. Set [short-circuit current](/Software/README.md#231-short-circuit) to 5x your rated battery current. For a 16s5P battery, with cells that support 10A max: 10A * 5P * 5 = 250A.
5. Set [section resistance](/Software/README.md#cell-resistance). If you know your cells internal resistance, use it. If you don't know it, use the one from the datasheet. If your cells fell of the back of a truck, assume internal resistance at 30mOhm. For a 16s5p battery with 30mOhm cells: 30mOhm/5P = 6mOhm.
6. Let the battery charge and balance the sections out. 
7. Don't skip steps, otherwise you will have bad battery data and wrong current cutoffs. 