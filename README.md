# pico-sample-project

A simple sample project for Raspberry Pi Pico (2 & W) boards.

Scripts have been tested only on Ubuntu.

## How to build & upload firmware

1. Install CMake (at least version 3.13), Python 3, a native compiler, and a GCC cross compiler
```
sudo apt install cmake python3 build-essential gcc-arm-none-eabi libnewlib-arm-none-eabi libstdc++-arm-none-eabi-newlib
```
2. Clone this repository and submodules:
```
$ git clone --recurse-submodules https://github.com/Crem2y/pico-console.git
```
3. Launch the build script:
```
./pico_build.sh
```
4. Press the reset button twice to enter bootloader mode.

5. Upload the generated `.uf2` file to your board.

6. (Optional) Launch the clean script to remove build artifacts:
```
./pico_clean.sh
```

## Sample Projects

### helloworld

This project provides a structure to add libraries.

It leaves only the folder without any libraries, so it's ideal as a base for simple projects.

### blink\_w

This project is for the Pico W board. The built-in LED is attached to the wireless module, not the RP2040, so it’s made separately for this case.

### blink\_rp2350

This project is for RP2350. It might be useful to enable building both in the future, depending on the options.

### pio\_test

PIO functionality requires assembling the `.pio` file, so I added it with a few changes to `CMakeLists.txt`.

## How to add library

Copy `lib_test` from the `lib` directory, rename it to the desired library name, and rename the `*.hpp`, `*.cpp` files accordingly.

Then, modify `CMakeLists.txt` in the `lib` directory to add the library.

## Script Usage

### pico\_build.sh

Generates a flashable binary in `.uf2` format (named after the project folder).

### pico\_clean.sh

Deletes the build folder inside the project folder.

## LICENSE

MIT license
