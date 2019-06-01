# robohatmm1-intro

documentation of my experiments with https://roboticsmasters.co/pages/robo-hat-mm1/

# 1 generate firmware following [mm1-hat-cpy-native](https://github.com/robotics-masters/mm1-hat-cpy-native/tree/master/firmware)

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

#path?#
make -j8 BOARD=robohatmm1_rev2

```
