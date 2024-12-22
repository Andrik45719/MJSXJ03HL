# Open source firmware on Xiaomi Mi Camera 2K Magnetic Mount (Ingenic T31)
# WARN! tested on T31N/T31ZL chipset with jxq03p sensor.
## Flashing [thingino firmware](https://github.com/themactep/thingino-firmware)
- Copy content of folder [SD_thingino](/SD_thingino) to FAT32 formatted SD-Card.
- Power off camera.
- Insert SD-Card into camera.
- Power on camera and wait until LED is white.
- Wait until LED is blinking (red->blue->white).
- Wait until camera resets about 3 minutes.
- Full fw backup will be saved to SD card as xiaomi_mjsxj03hl_t31XX_jxq03X.bin
- Connect to the camera Wi-Fi AP.
- Open http://172.16.0.1/ and setup camera.
- Apply settings and wait minute then powercycle it.

## Restore original firmware
- Copy xiaomi_mjsxj03hl_t31XX_jxq03X.bin to SD-Card and raname as autoupdate-full.bin
- Insert SD-Card into camera and power on it.
- Wait about 5 minutes.

# U-Boot
u-boot is modified version of (https://github.com/gtxaspec/u-boot-ingenic) isvp_t31_sfcnor_lite
- Added gpio_button=51i and gpio_mmc_power=54o into default env
- Removed CONFIG_RANDOM_MACADDR
- Fixed boot.scr source command call.

# thingino-firmware
## Determine SOC model
```
soc -m
```
## sysupgrade
```
fw_setenv osmem 52M@0x0; fw_setenv rmem 12M@0x3400000; reboot
```
```
sysupgrade -p
```
```
fw_setenv osmem 32M@0x0; fw_setenv rmem 32M@0x2000000; reboot
```
or
- download [thingino-firmware update](https://github.com/themactep/thingino-firmware/releases/download/firmware_update/thingino-xiaomi_mjsxj03hl_t31n_jxq03p-update.bin)
- copy it to FAT32 formatted SD-Card
- insert card into camera slot
- run:
```
flashcp /mnt/mmcblk0p1/thingino-xiaomi_mjsxj03hl_t31n_jxq03p-update.bin /dev/mtd5
```

 ## audio settings
 - PCM 16000
 - ALC 7
 - 
