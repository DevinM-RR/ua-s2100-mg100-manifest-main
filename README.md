# Regal Beloit BLE Gateway MG100 Firmware Manifest Repo

## Cloning Firmware

This is a Zephyr `west` manifest repository. To learn more about `west` see [here](https://docs.zephyrproject.org/latest/guides/west/index.html).

To clone this repository properly use the `west` tool. To install `west` you will first need Python3.

Install `west` using `pip3`:

```
# Linux
pip3 install --user -U west

# macOS (Terminal) and Windows (cmd.exe)
pip3 install -U west
```

Once `west` is installed, clone this repository using `west init` and `west update`:

```
# Checkout the latest manifest on main
west init -m git@github.com:LairdCP/regal_rexnord_mg100_manifest_2038.git --manifest-rev main

# Now, pull all the source described in the manifest
west update
```

## Preparing to Build

If this is your first time working with a Zephyr project on your computer you should follow the [Zephyr getting started guide](https://docs.zephyrproject.org/latest/getting_started/index.html#) to install all the tools.

The firmware uses zephyr 2.4.x, so GCC 9 is recommended.
[GNU Arm Embedded Toolchain: 9-2020-q2-update](https://developer.arm.com/tools-and-software/open-source-software/developer-tools/gnu-toolchain/gnu-rm/downloads) is recommended.

See here to [setup the GNU ARM Embedded tools](https://docs.zephyrproject.org/2.4.0/getting_started/toolchain_3rd_party_x_compilers.html#gnu-arm-embedded)

If using Linux, v0.11.4 of the Zephyr SDK is recommended.

## Building the Firmware

### VS Code

This project includes a .vscode settings directory with several configurations that add integration features with the VS Code editor. Use the Terminal->Run Task menu to see the tasks already defined for this project.

For example, here is a sequence of build task steps to build, sign and flash the merged bootloader and application to a mg100 board.

	build regal beloit with mcuboot
	flash regal app

To create a release, copy the following files from "ble\_gateway\_firmware\build\mg100\regal\zephyr" over to the "ble\_gateway\_firmware\Releases\<version>\mg100" folder (which may need to be manually created).
 
- application merged hex: **merged.hex**
- OTA application image binary: **app_update.bin**
- **zephyr.elf**

Rename them as desired (but for reference, the current naming scheme is:

- bootloader+application merged hex: **mg100-regal-<version>.hex**
- OTA application image binary: **mg100-regal-ota-<version>.bin **
