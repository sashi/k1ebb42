These instructions help you setup your K1 with EBB42 using M5P - No need U2C
Thanks to EricZimmerman [guides](https://github.com/EricZimmerman/VoronTools/tree/main) and Maz0r [work](https://github.com/maz0r/klipper_canbus)

## BOM
EBB42    
2x M3 Heatset Inserts (OD 4.2mm x L 3mm)  
4x M2 Heatset Inserts (OD 3.5mm x L 3mm)  
4x M2.5 x 3mm flat head screws  
2x M3 x 20mm screws  

## Flashing
### M5P
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
