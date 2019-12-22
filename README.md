# A IMU Demo
Dec 21st 2019

## 1. Connect 
your robohatmm1 to the usb port and wait to see the drive name CIRCUITPY

## 2. Copy 
all lib files [from](https://github.com/robotics-masters/mm1-hat-cpy-native/tree/master/USB/lib) to /lib on CIRCUITPY (the usb drive!)

![](https://github.com/Heavy02011/robohatmm1-intro/blob/master/images/libraryfiles_20191221.png)

## 2. Run
copy 
[imu.py test code](https://github.com/robotics-masters/RoboticsMasters_CircuitPython_MPU9250/blob/master/imu.py)
as code.py to CIRCUITPY

![](https://github.com/Heavy02011/robohatmm1-intro/blob/master/images/imu_test_code.png)

## 4. Show 
imu results

![](https://github.com/Heavy02011/robohatmm1-intro/blob/master/images/get_results_on_screen.png)


# B IMU running with Donkeycar
Dec 22st 2019

## 1. Have a look what I2C adresses are used
![](https://github.com/Heavy02011/robohatmm1-intro/blob/master/images/robohat_addr.png)

## 2. edit myconfig.py
```
# #9865, over rides only if needed, ie. TX2..
PCA9685_I2C_ADDR = 0x41 #0x40     #I2C address, use i2cdetect to validate this number
PCA9685_I2C_BUSNUM = 1 #None   #None will auto detect, which is fine on the pi. But other platforms should specify the bus num.

# #IMU
HAVE_IMU = True #False                #when true, this add a Mpu6050 part and records the data. Can be used with a 
  
# #ROBOHAT MM1
HAVE_ROBOHAT = True #False             #set to true when using the Robo HAT MM1 from Robotics Masters.  This will change to RC Control.

```

## 3. edit manage.py
correct the address of the IMU which is 0x69 for the robohat

![](https://github.com/Heavy02011/robohatmm1-intro/blob/master/images/robohat_ima_addr.png)

and the result after recording 
![](https://github.com/Heavy02011/robohatmm1-intro/blob/master/images/imu_sample_json.png)
