## Setup
### Install adb

Simply install adb using the builtin package manager

```
sudo apt install adb
```
### Enable adb support

Create file `/etc/udev/rules.d/51-android.rules` with content:

```
SUBSYSTEM=="usb", ATTR{idVendor}=="05a3", ATTR{idProduct}=="9331", MODE="0666", GROUP="plugdev"
```

This is necessary for the camera to be recognized by adb as a valid device.

## Operation
### motor_init

The camera has an initialization sequence, that resets its rotation to the middle point. It can be executed with

```
adb shell motor_init
```

### motor_rotate

The full range of motion of the camera appears to be divided into 4096 steps. We can rotate the camera relative to the current position using 

```
adb shell motor_rotate {steps}
```

Where `{steps}` is the number of steps we want to make. This value can be negative. If the exceeds the range of motion of the camera, it will hit the endstop, which should be avoided.

There is no builtin support for absolute positioning.

### Multiple cameras

All of the cameras have identical USB parameters, including the serial number, which makes them seemingly impossible to use with adb simultaneously.

However, adb has a `-t` option, which allows us to select devices using their transport ids, which are always unique (but change every time you plug in a device).

Current transport ids can be acquired with

```
adb devices -l
```
