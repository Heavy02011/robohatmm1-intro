# robohatmm1-intro

documentation of my experiments with https://roboticsmasters.co/pages/robo-hat-mm1/
see campaign https://www.crowdsupply.com/robotics-masters/robo-hat-mm1 for getting one

# 1 Learning Links (source: wallarug)

https://learn.adafruit.com/circuitpython-essentials/circuitpython-essentials


# 2 Generate firmware 

start using [the repo mm1-hat-cpy-native](https://github.com/robotics-masters/mm1-hat-cpy-native/tree/master/firmware)

original
```
git clone https://github.com/robotics-masters/mm1-hat-cpy-native
git clone https://github.com/adafruit/circuitpython/
cd circuitpython/
git submodule update --init --recursive
make -C mpy-cross
cd circuitpython/ports/atmel-samd
cp -r ../../../mm1-hat-cpy-native/firmware/mm1_hat_nonflash boards/mm1_hat_nonflash

make -j8 BOARD=mm1_hat_nonflash
```

list of boards directory
```
(carnd-tf16) rainer@neuron:~/dev/33-robohatmm1/circuitpython/ports/atmel-samd/boards$ ll
insgesamt 256
drwxr-xr-x 50 rainer rainer 4096 Jun  1 17:16 ./
drwxr-xr-x 14 rainer rainer 4096 Jun  1 17:19 ../
drwxr-xr-x  2 rainer rainer 4096 Jun  1 17:07 arduino_mkr1300/
drwxr-xr-x  2 rainer rainer 4096 Jun  1 17:07 arduino_mkrzero/
drwxr-xr-x  2 rainer rainer 4096 Jun  1 17:07 arduino_zero/
drwxr-xr-x  2 rainer rainer 4096 Jun  1 17:07 bast_pro_mini_m0/
-rw-r--r--  1 rainer rainer 1865 Jun  1 17:07 board.h
drwxr-xr-x  2 rainer rainer 4096 Jun  1 17:07 capablerobot_usbhub/
drwxr-xr-x  2 rainer rainer 4096 Jun  1 17:07 catwan_usbstick/
drwxr-xr-x  2 rainer rainer 4096 Jun  1 17:07 circuitplayground_express/
drwxr-xr-x  2 rainer rainer 4096 Jun  1 17:07 circuitplayground_express_crickit/
drwxr-xr-x  2 rainer rainer 4096 Jun  1 17:07 cp32-m4/
drwxr-xr-x  2 rainer rainer 4096 Jun  1 17:07 datalore_ip_m4/
drwxr-xr-x  2 rainer rainer 4096 Jun  1 17:07 escornabot_makech/
drwxr-xr-x  2 rainer rainer 4096 Jun  1 17:07 feather_m0_adalogger/
drwxr-xr-x  2 rainer rainer 4096 Jun  1 17:07 feather_m0_basic/
drwxr-xr-x  2 rainer rainer 4096 Jun  1 17:07 feather_m0_express/
drwxr-xr-x  2 rainer rainer 4096 Jun  1 17:07 feather_m0_express_crickit/
drwxr-xr-x  2 rainer rainer 4096 Jun  1 17:07 feather_m0_rfm69/
drwxr-xr-x  2 rainer rainer 4096 Jun  1 17:07 feather_m0_rfm9x/
drwxr-xr-x  2 rainer rainer 4096 Jun  1 17:07 feather_m0_supersized/
drwxr-xr-x  2 rainer rainer 4096 Jun  1 17:07 feather_m4_express/
drwxr-xr-x  2 rainer rainer 4096 Jun  1 17:07 feather_radiofruit_zigbee/
drwxr-xr-x  2 rainer rainer 4096 Jun  1 17:07 gemma_m0/
drwxr-xr-x  2 rainer rainer 4096 Jun  1 17:07 grandcentral_m4_express/
drwxr-xr-x  2 rainer rainer 4096 Jun  1 17:07 hallowing_m0_express/
drwxr-xr-x  2 rainer rainer 4096 Jun  1 17:07 itsybitsy_m0_express/
drwxr-xr-x  2 rainer rainer 4096 Jun  1 17:07 itsybitsy_m4_express/
drwxr-xr-x  2 rainer rainer 4096 Jun  1 17:07 kicksat-sprite/
drwxr-xr-x  2 rainer rainer 4096 Jun  1 17:07 meowmeow/
drwxr-xr-x  2 rainer rainer 4096 Jun  1 17:07 metro_m0_express/
drwxr-xr-x  2 rainer rainer 4096 Jun  1 17:07 metro_m4_airlift_lite/
drwxr-xr-x  2 rainer rainer 4096 Jun  1 17:07 metro_m4_express/
drwxr-xr-x  2 rainer rainer 4096 Jun  1 17:07 mini_sam_m4/
drwxr-xr-x  2 rainer rainer 4096 Jun  1 17:07 pewpew10/
drwxr-xr-x  2 rainer rainer 4096 Jun  1 17:07 pirkey_m0/
drwxr-xr-x  2 rainer rainer 4096 Jun  1 17:07 pybadge/
drwxr-xr-x  2 rainer rainer 4096 Jun  1 17:07 pygamer/
drwxr-xr-x  2 rainer rainer 4096 Jun  1 17:07 pyportal/
drwxr-xr-x  2 rainer rainer 4096 Jun  1 17:07 robohatmm1/
drwxr-xr-x  2 rainer rainer 4096 Jun  1 17:16 robohatmm1_rev2/
drwxr-xr-x  2 rainer rainer 4096 Jun  1 17:07 sam32/
-rw-r--r--  1 rainer rainer 2689 Jun  1 17:07 samd21x18-bootloader-crystalless.ld
-rw-r--r--  1 rainer rainer 2638 Jun  1 17:07 samd21x18-bootloader-external-flash-crystalless.ld
-rw-r--r--  1 rainer rainer 2622 Jun  1 17:07 samd21x18-bootloader-external-flash.ld
-rw-r--r--  1 rainer rainer 2651 Jun  1 17:07 samd21x18-bootloader.ld
-rw-r--r--  1 rainer rainer 2552 Jun  1 17:07 samd21x18-external-flash.ld
-rw-r--r--  1 rainer rainer 2549 Jun  1 17:07 samd21x18.ld
-rw-r--r--  1 rainer rainer 2660 Jun  1 17:07 samd51x18-bootloader-external-flash.ld
-rw-r--r--  1 rainer rainer 2660 Jun  1 17:07 samd51x19-bootloader-external-flash.ld
-rw-r--r--  1 rainer rainer 2719 Jun  1 17:07 samd51x19-bootloader.ld
-rw-r--r--  1 rainer rainer 2641 Jun  1 17:07 samd51x20-bootloader-external-flash.ld
-rw-r--r--  1 rainer rainer 2701 Jun  1 17:07 samd51x20-bootloader.ld
-rw-r--r--  1 rainer rainer 2506 Jun  1 17:07 samd51x20-external-flash.ld
-rw-r--r--  1 rainer rainer 2601 Jun  1 17:07 samd51x20.ld
drwxr-xr-x  2 rainer rainer 4096 Jun  1 17:07 sparkfun_lumidrive/
drwxr-xr-x  2 rainer rainer 4096 Jun  1 17:07 sparkfun_redboard_turbo/
drwxr-xr-x  2 rainer rainer 4096 Jun  1 17:07 sparkfun_samd21_dev/
drwxr-xr-x  2 rainer rainer 4096 Jun  1 17:07 sparkfun_samd21_mini/
drwxr-xr-x  2 rainer rainer 4096 Jun  1 17:07 trellis_m4_express/
drwxr-xr-x  2 rainer rainer 4096 Jun  1 17:07 trinket_m0/
drwxr-xr-x  2 rainer rainer 4096 Jun  1 17:07 trinket_m0_haxpress/
drwxr-xr-x  2 rainer rainer 4096 Jun  1 17:07 uchip/
drwxr-xr-x  2 rainer rainer 4096 Jun  1 17:07 ugame10/
```




my approach
```
git clone https://github.com/robotics-masters/mm1-hat-cpy-native
git clone https://github.com/adafruit/circuitpython/
cd circuitpython/
git submodule update --init --recursive
make -C mpy-cross

#cd circuitpython/ports/atmel-samd
cd circuitpython/ports/atmel-samd/boards/
(carnd-tf16) rainer@neuron:~/dev/33-robohatmm1/circuitpython/ports/atmel-samd$ 
cp -r ../../../mm1-hat-cpy-native/firmware/boards/robohatmm1_rev2/ boards/robohatmm1_rev2
```

compiling (???path???)
```
(carnd-tf16) rainer@neuron:~/dev/33-robohatmm1/circuitpython/ports/atmel-samd$
make -j8 BOARD=robohatmm1
```

output compiling
```
Use make V=1, make V=2 or set BUILD_VERBOSE similarly in your environment to increase build verbosity.
xargs: arm-none-eabi-gcc: Datei oder Verzeichnis nicht gefunden
../../py/mkrules.mk:81: recipe for target 'build-robohatmm1/genhdr/qstr.i.last' failed
make: *** [build-robohatmm1/genhdr/qstr.i.last] Error 127
make: *** Datei „build-robohatmm1/genhdr/qstr.i.last“ wird gelöscht
```


# 3 Arduino install (source: wallarug)

For Arduino, you can install the board definition file into Arduino IDE 1.8+ using the package_robohat_index.json file.

https://github.com/robotics-masters/mm1-hat-arduino/tree/master/custom_board
GitHub
robotics-masters/mm1-hat-arduino
Repository for storing Arduino related files and custom board definition. - robotics-masters/mm1-hat-arduino
The print output is in a serial port on your computer
use Putty or similar to connect to it.
