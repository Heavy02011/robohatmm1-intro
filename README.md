# robohatmm1-intro

documentation of my experiments with https://roboticsmasters.co/pages/robo-hat-mm1/
see campaign https://www.crowdsupply.com/robotics-masters/robo-hat-mm1 for getting one

# 1 Learning Links (source: wallarug)

https://learn.adafruit.com/circuitpython-essentials/circuitpython-essentials


# 2 Generate firmware 

start using [the repo mm1-hat-cpy-native](https://github.com/robotics-masters/mm1-hat-cpy-native/tree/master/firmware)

a. original approach
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

b. required additional setup according to [circuitpython repo](https://github.com/adafruit/circuitpython/tree/master/ports/atmel-samd)
```
sudo add-apt-repository ppa:team-gcc-arm-embedded/ppa
sudo apt-get install gcc-arm-embedded
```

c. my approach - preparing files
```
git clone https://github.com/robotics-masters/mm1-hat-cpy-native
git clone https://github.com/adafruit/circuitpython/
cd circuitpython/
git submodule update --init --recursive
make -C mpy-cross

cd circuitpython/ports/atmel-samd/boards/
cp -r ../../../mm1-hat-cpy-native/firmware/boards/robohatmm1_rev2/ boards/robohatmm1_rev2
cp -r ../../../mm1-hat-cpy-native/firmware/boards/robohatmm1/      boards/robohatmm1
```

d. list of boards directory
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

e. compiling
```
(carnd-tf16) rainer@neuron:~/dev/33-robohatmm1/circuitpython/ports/atmel-samd$
make -j8 BOARD=robohatmm1
make -j8 BOARD=robohatmm1_rev2
```

f. compiler output
```
(carnd-tf16) rainer@neuron:~/dev/33-robohatmm1/circuitpython/ports/atmel-samd$ 
make -j8 BOARD=robohatmm1

Use make V=1, make V=2 or set BUILD_VERBOSE similarly in your environment to increase build verbosity.
QSTR updated

19352 bytes free in flash out of 253440 bytes ( 247.5 kb ).
25776 bytes free in ram for stack out of 32768 bytes ( 32.0 kb ).

Converting to uf2, output size: 468480, start address: 0x2000
Wrote 468480 bytes to build-robohatmm1/firmware.uf2.

(carnd-tf16) rainer@neuron:~/dev/33-robohatmm1/circuitpython/ports/atmel-samd$ 
make -j8 BOARD=robohatmm1_rev2

Use make V=1, make V=2 or set BUILD_VERBOSE similarly in your environment to increase build verbosity.
QSTR updated

1724 bytes free in flash out of 187904 bytes ( 183.5 kb ).
25952 bytes free in ram for stack out of 32768 bytes ( 32.0 kb ).

Converting to uf2, output size: 372736, start address: 0x2000
Wrote 372736 bytes to build-robohatmm1_rev2/firmware.uf2.
```

g. installing firmware according to [the repo mm1-hat-cpy-native](https://github.com/robotics-masters/mm1-hat-cpy-native/tree/master/firmware)
```
- attach Robo HAT MM1 to your computer via USB.
- Double Tap 'reset' button to put board into UF2 Bootloader mode
- Copy firmware.uf2 from the build folder to the USB Drive called "ROBOBOOT".
- Wait for CircuitPython to be installed (about 5 seconds).
- Done.
```

# 3 short test with blinking led & printing before flashing

a. put this code in code.txt on the usb device called circuitpy
```
import board
import digitalio
import time

led = digitalio.DigitalInOut(board.D13)
led.direction = digitalio.Direction.OUTPUT

a = 0
while True:
    led.value = True
    time.sleep(1.5)
    led.value = False
    time.sleep(0.5)
    print('cool',a)
    a += 1
```

b. Connect over serial port

```
(carnd-tf16) rainer@neuron:~/dev/33-robohatmm1$ dmesg | grep tty
[    0.000000] console [tty0] enabled
[    0.513222] 00:01: ttyS0 at I/O 0x3f8 (irq = 4, base_baud = 115200) is a 16550A
[ 4856.235010] cdc_acm 1-5:1.0: ttyACM0: USB ACM device

(carnd-tf16) rainer@neuron:~/dev/33-robohatmm1$ 
sudo putty /dev/ttyACM0 -serial -sercfg 115200,8,n,1,N
```

### new, Dec 21st, 2019 

```
screen /dev/cu.usbmodem14601 115200 -L
```
[screen command on mac](https://software.intel.com/en-us/setting-up-serial-terminal-on-system-with-mac-os-x)


![putty output](https://github.com/Heavy02011/robohatmm1-intro/blob/master/images/codetxt-output1.png)

# 4 Installing MPU9250 imu library on board

a. clone driver into circuitpython
```
cd circuitpython/frozen/
git clone https://github.com/robotics-masters/RoboticsMasters_CircuitPython_MPU9250.git
```

b. tell make file to include libary
```
(carnd-tf16) rainer@neuron:~/dev/33-robohatmm1/circuitpython/ports/atmel-samd/boards/robohatmm3
vim mpconfigboard.mk:
FROZEN_MPY_DIRS += $(TOP)/frozen/RoboticsMasters_CircuitPython_MPU9250
```

c. make -j8 clean BOARD=robohatmm3

d. make -j8 BOARD=robohatmm3

e. install on board, see above

![imu output](https://github.com/Heavy02011/robohatmm1-intro/blob/master/images/imu.png)

# 5 Arduino install (source: wallarug)

For Arduino, you can install the board definition file into Arduino IDE 1.8+ using the package_robohat_index.json file.

https://github.com/robotics-masters/mm1-hat-arduino/tree/master/custom_board
GitHub
robotics-masters/mm1-hat-arduino
Repository for storing Arduino related files and custom board definition. - robotics-masters/mm1-hat-arduino
The print output is in a serial port on your computer
use Putty or similar to connect to it.

a. open Arduino IDE

b. open preferences and enter under section custom boards url
```
https://raw.githubusercontent.com/robotics-masters/mm1-hat-arduino/master/custom_board/package_robohat_index.json
```
c. open board manager

d. select robohat to install

![board manager](https://github.com/Heavy02011/robohatmm1-intro/blob/master/images/install-arduino.png)

e. setup interface: /dev/ttyACM0 (in my case)

f. select robohat as board

g. have fun with the Arduino part

PS. installing Arduino from https://www.arduino.cc/ helps to simplify setting group permissions for dialout etc yourself
