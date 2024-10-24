# MJSXJ03HL
OpenIPC on MJSXJ03HL
## U-Boot
### FW Backup
```
mw.b 0x80600000 0xff 0x1000000
sf probe 0; sf read 0x80600000 0x0 0x1000000
mmc dev 0; mmc erase 0x10 0x8000; mmc write 0x80600000 0x10 0x8000

# Use the following command to restore the backup to a file on a PC
# (replace /dev/sdc with your SD card device):
# sudo dd bs=512 skip=16 count=32768 if=/dev/sdc of=./fulldump.bin
```
### Flash OpenIPC FW
```
gpio clear 54 ; mmcinfo

mw.b 0x80600000 0xff 0x1000000
fatload mmc 0:1 0x80600000 openipc-t31n-lite-16mb.bin
sf probe 0
sf erase 0x0 0x1000000; sf write 0x80600000 0x0 0x1000000
reset
```

## Camera setup

```
firstboot

fw_setenv osmem 34M
fw_setenv rmem 30M@0x2200000
fw_setenv extras nogmac
fw_setenv wlandev rtl8189fs-generic
fw_setenv wlanssid wifi
fw_setenv wlanpass password


gpio clear 54
echo "INSERT" > /sys/devices/platform/jzmmc_v1.2.0/present

cd /mnt/mmcblk0p1/
cp -rv ./files/* /

echo "extra/8189fs.ko: kernel/net/wireless/cfg80211.ko" | tee -a /lib/modules/3.10.14__isvp_swan_1.0__/modules.dep
```

```
sysupgrade --url=https://github.com/OpenIPC/builder/releases/download/latest/t31_lite_xiaomi-mjsxj03hl-nor.tgz -k -r -z
```

```
sysupgrade --url=https://github.com/OpenIPC/builder/releases/download/latest/t31_lite_xiaomi-mjsxj03hl-jxq03-nor.tgz -k -r -z
```
