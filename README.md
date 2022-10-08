
***
# XROCK
The low level tools for rockchip SOC with maskrom and loader mode support.

## How to build

### Linux platform

Arch Linux is installed through the AUR repository:

```shell
# Release version
yay -S xrock

# Development version
yay -S xrock-git
```

The xrock tools depends on the `libusb-1.0` library, you need to install `libusb-1.0-0-dev` before compile, for example in ubuntu:

```shell
sudo apt install libusb-1.0-0-dev
```

Then just type `make` at the root directory, you will see a binary program.

```shell
cd xrock
make
sudo make install
```

### Window platform

Install some build tools

```shell
sudo apt install mingw-w64
sudo apt install autoconf
sudo apt install libtool-bin
```

Download and install libusb

```shell
git clone https://github.com/libusb/libusb.git
cd libusb
./autogen.sh
./configure --host=i686-w64-mingw32 --prefix=/usr/i686-w64-mingw32/
make
sudo make install
```

Build xrock source code

```shell
cd xrock
CROSS=i686-w64-mingw32- make
```

For 64-bits windows, you can using `x86_64-w64-mingw32-` instead of `i686-w64-mingw32` above.


## Usage

```shell
usage:
    xrock maskrom <ddr> <usbplug> [--rc4-off] - Initial chip using ddr and usbplug in maskrom mode
    xrock version                             - Show chip version
    xrock capability                          - Show capability information
    xrock reset [maskrom]                     - Reset chip to normal or maskrom mode
    xrock hexdump <address> <length>          - Dumps memory region in hex
    xrock dump <address> <length>             - Binary memory dump to stdout
    xrock read <address> <length> <file>      - Read memory to file
    xrock write <address> <file>              - Write file to memory
    xrock exec <address>                      - Call function address
    xrock flash                               - Detect flash and show information
    xrock flash erase <sector> <count>        - Erase flash sector
    xrock flash read <sector> <count> <file>  - Read flash sector to file
    xrock flash write <sector> <file>         - Write file to flash sector
```

## Tips

- The maskrom command can only used in maskrom mode, Before executing other commands, you must first execute the maskrom command

- The memory base address from 0, **NOT** sdram's physical address.

### RV1106

```shell
sudo xrock maskrom rv1106_ddr_924MHz_v1.09.bin rv1106_usbplug_v1.06.bin --rc4-off
sudo xrock version
```

### RK1808

```shell
sudo xrock maskrom rk1808_ddr_933MHz_v1.05.bin rk1808_usbplug_v1.05.bin
sudo xrock version
```

### RK3128

```shell
sudo xrock maskrom rk3128_ddr_300MHz_v2.12.bin rk3128_usbplug_v2.63.bin
sudo xrock version
```

### RK3288

```shell
sudo xrock maskrom rk3288_ddr_400MHz_v1.11.bin rk3288_usbplug_v2.63.bin
sudo xrock version
```

### RK3399

```shell
sudo xrock maskrom rk3399_ddr_800MHz_v1.25.bin rk3399_usbplug_v1.26.bin
sudo xrock version
```

### RK3399PRO

```shell
sudo xrock maskrom rk3399pro_ddr_666MHz_v1.25.bin rk3399pro_usbplug_v1.26.bin
sudo xrock version
```

### PX30

```shell
sudo xrock maskrom px30_ddr_333MHz_v1.16.bin px30_usbplug_v1.31.bin
sudo xrock version
```

### RK3308

```shell
sudo xrock maskrom rk3308_ddr_589MHz_uart2_m1_v1.31.bin rk3308_usbplug_v1.27.bin
sudo xrock version
```

### RK3566

```shell
sudo xrock maskrom rk3566_ddr_1056MHz_v1.11.bin rk356x_usbplug_v1.13.bin --rc4-off
sudo xrock version
```

### RK3568

```shell
sudo xrock maskrom rk3568_ddr_1560MHz_v1.11.bin rk356x_usbplug_v1.13.bin --rc4-off
sudo xrock version
```

### RK3588

```shell
sudo xrock maskrom rk3588_ddr_lp4_2112MHz_lp5_2736MHz_v1.05.bin rk3588_usbplug_v1.07.bin --rc4-off
sudo xrock version
```

## Links

* [The rockchip loader binaries](https://github.com/rockchip-linux/rkbin)
* [The rockchip rkdeveloptool](https://github.com/rockchip-linux/rkdeveloptool)

## License

This library is free software; you can redistribute it and or modify it under the terms of the MIT license. See [MIT License](LICENSE) for details.

