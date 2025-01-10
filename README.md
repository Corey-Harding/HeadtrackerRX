# BT-PPM Module
Bluetooth receiver for Headtracker on FRSky Para protocol  
Based on BTWifiModule by dlktdr (https://github.com/dlktdr/BTWifiModule)  
HeadtrackerRX Fork by Egor812 (https://github.com/Egor812/HeadtrackerRX)  
Readme Translated to English - Compiled firmware located as artifacts under github actions  

## Description
We receive data from HeadTracker via Bluetooth using the FRSky Para protocol. In my case, https://github.com/ysoldak/HeadTracker is used on Seed Studio nRF52840 Sense. We send data to the PPM trainer connector.  

Needed by those who don't want to solder a BT receiver into the equipment.  

## Soldering Connector for Trainer
Seed Studio XIAO-ESP32C3  
```
Jack 3.5 4pin TRRS  
|= = = >  
 A B C D  
A - not used
B and C - GND  
D - PPM - D0  
```
Or  
```
Jack 3.5mm Mono TS  
|=== >  
  A  D  
A - GND  
D - D0  
```
Note: D0 is likely GPIO2  

## Hardware settings
Model-Setup-Trainer mode Master/Jack  
Sys-Trainer - channels and trimmers.  

## Flash Firmware
```The latest precompiled firmware files can be downloaded by clicking on ACTIONS above, selecting a recent workflow and downloading the firmware file listed under ARTIFACTS, eventually after some testing I will upload them to the releases page, for now you must be logged in to view github actions artifacts```  
Web Flash Tool by Spacehuhn (https://esp.huhn.me/)  
Click ERASE and when completed select  
```
0x0 bootloader.bin  
0x8000 partitions.bin  
0x10000 firmware.bin
```
Click PROGRAM, wait for it to complete, then press reset on the board and enter a serial monitor  

## Setting up the receiver
Connect via USB. In serial monitor:  
Web Serial Monitor by Spacehuhn (https://serial.huhn.me/)  
Enter the command ```AT+DISC?```  
Find the transmitter address in the list. Enter ```AT+CONaddress```MACaddressHERE  
For Example: ```AT+CONDCB116851608```  
Now this receiver will automatically connect to this transmitter  

## Note
Performance tested only on ESP32C3  
