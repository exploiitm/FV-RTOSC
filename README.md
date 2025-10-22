# FV-RTOSC

## Dependencies

Clone the `pico-sdk` repository alongside the project directory

```bash
git clone https://github.com/raspberrypi/pico-sdk.git --branch master
cd pico-sdk
git submodule update --init
cd ..
```

For building the projects you'll need CMake and ARM GNU Toolchain

### Arch Linux
`sudo pacman -S arm-none-eabi-gcc arm-none-eabi-newlib cmake `

## Building

This project has been tested only for the Raspberry Pi Pico 2W. For other boards modify the `DPICO_BOARD` option.

You need to set the `PICO_SDK_PATH` environment variable.

```bash
mkdir build
cd build
export PICO_SDK_PATH=../../pico-sdk
cmake -DPICO_BOARD=pico2_w ..
make
```

### For LSP Support (clangd)

Pass `DCMAKE_EXPORT_COMPILE_COMMANDS=ON` to CMake and link `compile_commands.json` to project root.

```bash
mkdir build
cd build
export PICO_SDK_PATH=../../pico-sdk
cmake -DPICO_BOARD=pico2_w -DCMAKE_EXPORT_COMPILE_COMMANDS=ON ..
cd ..
ln -sf build/compile_commands.json compile_commands.json
```
