# Open source firmware on Xiaomi Mi Camera 2K Magnetic Mount (Ingenic T31)
# WARN! tested on T31N/T31ZL chipset with jxq03p sensor.
## U-Boot update
- Copy content of folder SD_uboot to FAT32 formated SD-Card.
- Power off camera.
- Insert SD-Card into camera press and hold reset.
- Power on camera and wait until LED is white.
- Wait until LED is Orange.
- Reset camera by power cycle.
- Wait until Blue LED (Linux image backup done).
- Power off camera and remoce SD-Card.
- Copy fwbkup.bin somewhere into secure place.
  
## Flashing [thingino firmware](https://github.com/themactep/thingino-firmware)
- Remove all files on SD-Card.
- Copy content of folder SD_thingino-xiaomi_mjsxj03hl_t31n_jxq03p ro SD-Card root.
- Insert SD-Card into camera and power on it.
- Wait about 5 minutes until IR shutter clicks and blue LED flashing.
- Connect to the camera Wi-Fi AP.
- Open http://172.16.0.1/ and setup camera.
- Apply settings and wait minute then powercycle it.

## Restore original firmware
- Copy fwbkup.bin to SD-Card and raname as autoupdate-full.bin
- Insert SD-Card into camera and power on it.
- Wait about 5 minutes.


# U-Boot
u-boot is modified version of (https://github.com/gtxaspec/u-boot-ingenic) isvp_t31_sfcnor_lite
- Added gpio_button=51i and gpio_mmc_power=54o into default env
- Removed CONFIG_RANDOM_MACADDR
- Fixed boot.scr source command call.

## Determine SOC model
```
soc -m
```
