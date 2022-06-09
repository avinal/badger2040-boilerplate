# Badger 2040 C++ Boilerplate Project

This repository extends the [boilerplate](https://github.com/pimoroni/pico-boilerplate) project created by Pimoroni specifically to be used as a boilerplate for Badger 2040 C++ projects.

## Prerequisite

I have gathered all the required dependencies for developing C++ programs for Badger 2040 and created a [bootstrap](./bootstrap) script to do the heavy lifting. However, the prerequisites are as listed below.

- Common dependencies
  - `git`
  - `cmake`
  - `make`
  - `ninja-build`
- Build dependencies for Fedora
  - `gcc-arm-linux-gnu`
  - `arm-none-eabi-gcc-cs-c++`
  - `arm-none-eabi-gcc-cs`
  - `arm-none-eabi-binutils`
  - `arm-none-eabi-newlib`
- Build dependencies for Ubuntu
  - `gcc-arm-none-eabi`
  - `build-essential`
  - `gcc-arm-none-eabi`
- Project dependencies
  - [pimoroni-pico](https://github.com/pimoroni/pimoroni-pico)
  - [pico-extras](https://github.com/raspberrypi/pico-extras)
  - [pico-sdk](https://github.com/raspberrypi/pico-sdk)

## Project Related FAQs

### How to create a new Badger 2040 program?

This part explains how to properly arrange source code for a Badger 2040 program for easy compiling and maintenance.

1. Clone the unmodified [programexample](./programexample/) directory and rename it (let it be `example-too`).
2. Add your source code files to the directory.
3. Modify the [CMakeLists.txt](./programexample/CMakeLists.txt) in the new program directory to add source files and required options.
4. Add the following line at the end of this project's [CMakeLists.txt](./CMakeLists.txt)

   ```cmake
   add_subdirectory(example-too)
   ```

### How to build the program?

If you have used the supplied **bootstrap** script, you should be able to see the build folder, please follow from steps in that case.

1. Install all the build dependencies for your distro and initialize all the submodules. Run the following command in the project root and then inside all three submodules `pico-sdk`, `pico-extras`, `pimoroni-pico`.

    ```bash
    git submodule update --init
    ```

2. Create a `build` directory.

   ```bash
   mkdir build && cd build
   ```

3. Generate CMake project. (_Note: using Ninja for speedy compilation._)

   ```bash
   cmake .. -DPICO_BOARD=pimoroni_badger2040 -GNinja
   ```

4. Compile your project. Do not compile the whole project, only compile the project you need by specifying the name.

   ```bash
   ninja <program-name>
   ```

### How to flash the programs to Badger 2040?

The Badger 2040 uses `.ef2` files to flash any program. You can upload MicroPython, CircuitPython or custom-built images. Follow these steps to use your custom build images. You can add only one file at a time.

1. Hold `boot/usr` button on your badger and connect to your system. It will get mounted as **RPI-RP2**. There will be two files already, _do not touch them_.
2. Go to the build directory and find the corresponding `<project-name>.ef2` file for your project.
3. Copy this file to the mounted **RPI-RP2**.
4. Your badger screen will flash and the program will load.
5. You can now test your program.

## References

### Where to buy Badger 2040?

- [India](https://theelectronics.shop/product/badger-2040-badger-only/)
- [WorldWide](https://shop.pimoroni.com/products/badger-2040)

### Important Repositories

- [Raspberry Pi Pico SDK](https://github.com/raspberrypi/pico-sdk)
- [Pimoroni Pico Libraries and Examples](https://github.com/pimoroni/pimoroni-pico)
- [Raspberry Pi Pico Additional Library](https://github.com/raspberrypi/pico-extras)

### Acknowledgments

- [Original Pico C++ Boilerplate Project](https://github.com/pimoroni/pico-boilerplate)
- [Compiling Raspberry Pi Pico C/C++ programs on Fedora by John Walicki](https://github.com/johnwalicki/RaspPi-Pico-Examples-Fedora)
- [The Badger Set - small C++ programs for the Badger2040 by Michael Bell](https://github.com/MichaelBell/badger-set)

## License

I've added the BSD 3-Clause License to match the license used in the project dependencies. You should review this and check it's appropriate for your project before publishing your code.
