```
extract rootfs.tar.bz2 into /root/factory_t31_ZMC6tiIDQN/rootfs

cd ./thingino-firmware
./user-menu.sh

Main Menu -> linux-menuconfig -> linux-menuconfig -> xiaomi_mjsxj03hl_t31n_jxq03p

General setup ->
  Initial RAM filesystem and RAM disk (initramfs/initrd) support 
    /root/factory_t31_ZMC6tiIDQN/rootfs
Using LZMA

Kernel hacking ->
  Built-in kernel command line
console=ttyS1,115200n8 mem=42M@0x0 rmem=22M@0x2A00000 init=/init mtdparts=jz_sfc:256K(boot),16384k@0(all)

  Built-in command line overrides firmware arguments


/images/uImage  -> factory_t31_ZMC6tiIDQN 
```
