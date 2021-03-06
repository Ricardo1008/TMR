Introductions :
===================================

### Resources

 *  User Guide :
 
           TMR_FC_UM_V1_120730.pdf

 *  Sechematic :
 
          TMR_FC_HW_V1_120830.pdf

 *  Gerber :

           TMRFC_GB_V1_120930.rar

 *  Software :

           The software is Porting from "PX4".
           https://github.com/cctsao1008/TMR
         
### Get source code :
    
 > pi@raspberry：/x $ cd x: ( ex. )
 
 > pi@raspberry：/x $ git clone git@github.com:cctsao1008/TMR.git
       
           Cloning into 'TMR'...
           remote: Counting objects: 11, done.
           remote: Compressing objects: 100% (10/10), done.
           remote: Total 11 (delta 3), reused 5 (delta 1)
           Receiving objects: 100% (11/11), done.

 > pi@raspberry：/x $ cd cd TMR/
 
 > pi@raspberry：/x/TMR (master)$ git submodule update --init --recursive
 
           Submodule 'Bootloader' (git@github.com:cctsao1008/Bootloader.git) registered for path 'Bootloader'
           Submodule 'Firmware' (https://github.com/cctsao1008/Firmware) registered for path 'Firmware'
           Submodule 'libopencm3' (git@github.com:cctsao1008/libopencm3.git) registered for path 'libopencm3'
           Cloning into 'Bootloader'...
           remote: Counting objects: 148, done.
           remote: Compressing objects: 100% (50/50), done.

           Receiving objects: 100% (148/148), 52.83 KiB | 19 KiB/s, done.
           Resolving deltas: 100% (96/96), done.
           Submodule path 'Bootloader': checked out 'fd53d28c0760c54e93f230f6aafbc99ee09045dc'
           Cloning into 'Firmware'...
           remote: Counting objects: 80335, done.
           remote: Compressing objects: 100% (16927/16927), done.
           remote: Total 80335 (delta 62860), reused 80332 (delta 62857)
           Receiving objects: 100% (80335/80335), 46.40 MiB | 2.40 MiB/s, done.
           Resolving deltas: 100% (62860/62860), done.
           Submodule path 'Firmware': checked out 'f3fb6509cdf873100c1fe4d0bc379177216c70bc'
           Submodule 'NuttX' (git@github.com:cctsao1008/NuttX.git) registered for path 'NuttX'
           Cloning into 'NuttX'...
           remote: Counting objects: 130874, done.
           remote: Compressing objects: 100% (23609/23609), done.
           remote: Total 130874 (delta 106319), reused 130874 (delta 106319)
           Receiving objects: 100% (130874/130874), 32.98 MiB | 79 KiB/s, done.
           Resolving deltas: 100% (106319/106319), done.
           Submodule path 'NuttX': checked out '56433ad9238ccfd7fe3ba3bd1a050ef785dfaea5'
           Cloning into 'libopencm3'...
           remote: Counting objects: 7300, done.
           remote: Compressing objects: 100% (3341/3341), done.
           remote: Total 7300 (delta 3741), reused 7300 (delta 3741)
           Receiving objects: 100% (7300/7300), 1.61 MiB | 74 KiB/s, done.
           Resolving deltas: 100% (3741/3741), done.
           Submodule path 'libopencm3': checked out '3d3c6d8abf7407f605e0afd1eed533eeb5a3dbb2'

### Hardware Features

  *  MCU : 

           STM32f405RG

  *  AHRS :

           MPU6050, HMC5883, MS5611

  *  Features :

           12 channels PWM output, one PPM input and one Futaba S.BUS input,
           Built-in 10 DOF, 5 LEDs ( controlled by PCA9533/9536), GPS port ( UART / I2C),
           Auxiliary SPI and  GPIO, RF port (APC230 or BT), LiPo Voltage measure via ADC,
           Beeper for tone alarm, SWD port, SONAR, USB VCP and MSC, Micro SD ( can be read via USB),
           Light Bar LED control, Internal FLASH EEPROM emulation using sector 1, 2 and 3 ( 16KB x 3 ),
           RTC ( power keep by 3V CR1220 )
           ....... etc

  *  Stress Test VB scripts :

           Auto re-boot loop test, tone alarm loop test, ..... etc

  *  Support PX4 Qupgrade tool :


Firmware update steps :
===================================

###   Update bootloader

    sudo dfu-util -a 0 -d 0x0483:0xdf11 --dfuse-address 0x08000000 -D tmrfc_bl.bin

###   Update OS image

  * Optinn 1 : Using "dfu-util"

    sudo dfu-util -a 0 -d 0x0483:0xdf11 --dfuse-address 0x08004000 -D tmrfc-v1_default.bin

  * Option 2 : Using "QUpgrade"

    Note :  To using "QUpgrade" if you have " tmrfc_bl.bin" been pre-flashed !!! 

    1. Get the tool :  (https://pixhawk.ethz.ch/px4/downloads)<br />
    2. Open "QUpgrade" tool
    3. Select "Advanced"
    4. Select your "tmrfc-v1_default.px4"
    5. Click "Flash"
    6. Connect your TMRFC board via USB, OR click "RESET" key on TMRFC board

Enjoy your TMR-FC !!



If you need further information or assistance please revert.

Sincerely yours.

TSAO, CHIA-CHENG ( chiacheng.tsao@gmail.com )

