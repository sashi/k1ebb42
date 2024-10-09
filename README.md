These instructions help you setup your K1 with EBB42 v1.1, v.1.2 using M5P - No need U2C
Thanks to EricZimmerman [guides](https://github.com/EricZimmerman/VoronTools/tree/main) and Maz0r [work](https://github.com/maz0r/klipper_canbus)

## BOM
EBB42    
2x M3 Heatset Inserts (OD 4.2mm x L 3mm)  
4x M2 Heatset Inserts (OD 3.5mm x L 3mm)  
4x M2.5 x 3mm flat head screws  
2x M3 x 20mm screws  

## M5P
1. Clone Katapult to your Pi  

```
cd ~  
git clone https://github.com/Arksine/katapult
```  
2. Run the following commands to bring up the menu to configure the firmware  
```
cd katapult
make menuconfig
```  
3. Starting from the top, make your firmware selections look exactly like the image below  
![m5pkatapult](img/m5pkatapult.png)  
4. Exit using ESC or Q, then confirm with yes (Y)  
5. Build the firmware using the following commands:  
```
make clean
make
```
If no errors continue  
6. Run the following commands to bring up the menu to configure the firmware (Klipper)
```
cd ~/klipper
make menuconfig
```
7. Starting from the top, make your firmware selections look exactly like the image below
![klipperm5p](img/klipperm5p.png)  
8. Exit using ESC or Q, then confirm with yes (Y)  
9. Build the firmware using the following commands:
```
make clean
make
```
If no errors continue  

## Flashing Klipper to M5P
1. With power on the M5P side of the board, press and hold down the boot button then click the reset button, allow a secund or two to pass then release the boot button  
2. Run ``lsusb``  
3. Look for STM in DFU Mode in the output text then proceed, if not try step 1 again  
4. Run the following to flash katapult to M5P  
```
sudo dfu-util -a 0 -D ~/katapult/out/canboot.bin --dfuse-address 0x08000000:force:mass-erase -d 0483:df11
```
If no errors proceed  (If you see any mention of an error after the File downloaded successfully message, it can be ignored)  
![flashok](img/flashok.png)

5. Run the following to flash klipper to M5P
```
sudo dfu-util -a 0 -D ~/klipper/out/klipper.bin --dfuse-address 0x08002000:leave -d 0483:df11
```
If no errors proceed and click the reset button  the M5P (If you see any mention of an error after the File downloaded successfully message, it can be ignored>  
![flashok](img/flashok.png)

## Building and Flashing for EBB42

1. Run the following commands to bring up the menu to configure the firmware  
```
cd ~/katapult
make menuconfig
``` 

2. Starting from the top, make your firmware selections look exactly like the image below  
![katapultebb](img/katapultebb.png)  
3. Exit using ESC or Q, then confirm with yes (Y)  
4. Build the firmware using the following commands:  
```
make clean
make
```
If no errors continue  

5. Run the following commands to bring up the menu to configure the firmware  (Klipper)
```
cd ~/klipper
make menuconfig
``` 
6. Starting from the top, make your firmware selections look exactly like the image below  
![klipperebb](img/klipperebb.png)  
4. Plug in a USB-C cable from the EBB42 to your Pi and set the USB jumper
![jumper](img/jumper.jpg)  
5. Hold down the boot button and press the reset button, wait a second or two and then release the boot button  
6. Run ``lsusb``  
7. Look for STM in DFU Mode in the output text then proceed, if not try step 2 again  
8. Run the following to flash Katapult to EBB42
```
sudo dfu-util -a 0 -D ~/katapult/out/canboot.bin --dfuse-address 0x08000000:force:mass-erase -d 0483:df11
```
If no errors proceed and click the reset button  the M5P (If you see any mention of an error after the File downloaded >  message, it can be ignored.  
![flashok](img/flashok.png)
