```C
//speaker_ctl.ko 
int speakerctl_ioctl(struct file *f, unsigned int cmd)
{
  int ret; // $v0
  const char *str; // $a0

  if ( *(_DWORD *)(*((_DWORD *)f + 28) + 52) )
  {
    ret = 0;
    switch ( cmd )
    {
      case 0u:
        gpio_direction_output(63);
        _udelay(600);
        str = "SPEAKER CTL MODE0 !\n";
        goto exit;
      case 1u:
        gpio_direction_output(63);
        _udelay(600);
        gpio_direction_output(63);
        _udelay(100);
        str = "SPEAKER CTL MODE1 !\n";
        goto exit;
      case 2u:
        gpio_direction_output(63);
        _udelay(600);
        gpio_direction_output(63);
        _udelay(5);
        gpio_direction_output(63);
        _udelay(5);
        gpio_direction_output(63);
        _udelay(100);
        str = "SPEAKER CTL MODE2 !\n";
        goto exit;
      case 3u:
        gpio_direction_output(63);
        _udelay(600);
        gpio_direction_output(63);
        _udelay(5);
        gpio_direction_output(63);
        _udelay(5);
        gpio_direction_output(63);
        _udelay(5);
        gpio_direction_output(63);
        _udelay(5);
        gpio_direction_output(63);
        _udelay(100);
        str = "SPEAKER CTL MODE3 !\n";
        goto exit;
      case 4u:
        gpio_direction_output(63);
        _udelay(600);
        gpio_direction_output(63);
        _udelay(5);
        gpio_direction_output(63);
        _udelay(5);
        gpio_direction_output(63);
        _udelay(5);
        gpio_direction_output(63);
        _udelay(5);
        gpio_direction_output(63);
        _udelay(5);
        gpio_direction_output(63);
        _udelay(5);
        gpio_direction_output(63);
        _udelay(100);
        str = "SPEAKER CTL MODE4 !\n";
exit:
        printk(str);
        ret = 0;
        break;
      default:
        return ret;
    }
  }
  else
  {
    printk("Please Open /dev/speakerctl Firstly\n");
    return -1;
  }
  return ret;
}
```
