# stm32loader

In case you fried your SWDIO/CLK pins you could still use this tool
to burn firmware to MCU:

* convert ELF to BIN:

```bash
arm-none-eabi-objcopy -S -O binary build_elf out.bin
```

* connect serial port to pins PA9/10
* set BOOT0 pin to 1 and turn to power on/reset the device
* burn resulting BIN-file:

```bash
python2 stm32loader.py -p /dev/ttyUSB0 -f F3 -e -w -v out.bin
```

* set BOOT0 back to 0 and reset.
