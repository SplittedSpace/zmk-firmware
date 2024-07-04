## Install and build

```
# Prepare
west init -l app/

# Project root directory
cd ./app

# Build Harper firmware
mkdir ../.builds/harper
west build -d build/harper/left -b harper_left -p && cp ./build/harper/left/zephyr/zmk.uf2 ../.builds/harper/harper_left.uf2
west build -d build/harper/right -b harper_right -p && cp ./build/harper/right/zephyr/zmk.uf2 ../.builds/harper/harper_right.uf2
```


```
* check version: arm-none-eabi-gdb --batch -ex "target extended-remote /dev/tty.usbmodem348D377F31351" -ex "monitor"
* unlock: arm-none-eabi-gdb --batch -ex "target extended-remote /dev/tty.usbmodem348D377F31351" -ex "mon swdp_scan" -ex "att 1" -ex "mon erase_mass"
* flash: arm-none-eabi-gdb --batch -ex "target extended-remote /dev/tty.usbmodem348D377F31351" -ex "mon swdp_scan" -ex "file pca10056_bootloader-0.5.0-dirty_s140_6.1.1.hex" -ex "att 1" -ex "mon erase" -ex load

```


## Manual Firmware changes

```
https://github.com/zmkfirmware/zmk/pull/1120/files#diff-7c4c10cb572fb4f013f3aab5c389b3e3a1c71d716185333769d0f979cf515976
```
