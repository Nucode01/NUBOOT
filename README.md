# 🚀 NuBoot

Welcome to the NuBoot repository, the bootloader solution for NuCode products.

## 📝 Overview

NuBoot is a highly efficient and lightweight bootloader derived from MCUboot, optimized for minimal flash usage. It is designed to support a wide range of NuCode products, ensuring seamless firmware updates and secure boot processes.

## 🛠️ Supported Boards

### Officially Supported:
- **NU40-B-Dev02 Development Kit**

### Compatible Boards:
- **nrf52840dk**

## 🔥 Bootloader Flashing Guide

Instructions for flashing the bootloader are available in the `guidelines` folder. 
Each guide is tailored to the specific board it supports.

## 💻 Firmware Programming with NuBoot

Follow these steps to program your firmware using NuBoot. For detailed instructions, refer to the specific board programming guidelines.

### 1. 🛠️ Prepare Compatible Firmware
Build the firmware using the following command:
```sh
west build -b $BOARD_NAME -p -- -DCONFIG_BOOTLOADER_MCUBOOT=y
```

### 2. 🔄 Enter Recovery Mode
- Connect the board to your computer via USB.
- Hold button S1 (P0.11) before powering up or while pressing the reset button.

### 3. 🔍 Identify COM Port
Open Device Manager (Windows) and locate the board's COM port under "USB Serial Device."

### 4. ⚙️ Configure `mcumgr`
Add a connection using the detected COM port:
```sh
mcumgr conn add connection_name type="serial" connstring="dev=COM8,baud=115200,mtu=512"
```
*(Replace `COM8` with the actual COM port.)*

### 5. 📤 Flash Firmware
Upload the new firmware image:
```sh
mcumgr -c connection_name image upload .\build\zephyr\app_update.bin
```
> Note: Only `app_update.bin` is supported for flashing.

### 6. 🔄 Apply Firmware
Reset the device to apply the new firmware:
```sh
mcumgr -c connection_name reset
```
Or press the reset button.

## 📚 Additional Resources

For more information and advanced usage, refer to the following resources:
- [MCUboot Project](https://github.com/mcu-tools/mcuboot)
- [mynewt-mcumgr](https://github.com/apache/mynewt-mcumgr)
- [nRF SDK](https://github.com/nrfconnect/sdk-nrf)

## 🧑‍🤝‍🧑 Support

For more details, support, or troubleshooting, please contact [huu.nghia@easypcb.vn](mailto:huu.nghia@easypcb.vn).
