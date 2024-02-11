# RP2040
A very fast dual core processor that's cheap, available, and has good software support.  
  
## Features and Limitations
- No CAN, must use MCP25625 SPI-CAN interface
- 125MHz dual core
- No floating point hardware
- CMake build system
- USB flashing ability
- PIO peripheral is incredibly powerful
  
Trivial setup on linux, annoying on Windows.
  


## Programming Methods
- USB programming
    - By pulling the QSPI flash chip select line low upon powerup the device will open as a USB Mass Storage Device (like a flash drive), where a user can drag and drop a `.uf2` file (compiled binary) into it. The RP2040 will reboot and execute the loaded code.

- 2 Wire Debug
    - Through the use of openocd/picotool, typically done via picoprog a `.elf` (compiled binary) can be loaded via the SWD pins into the processor

## Toolchain Setup
Linux systems with apt can simply run `pico_setup.sh` provided by the Raspberry Pi Foundation.  
Windows users should follow Shawn Hymel's excellent guide. Use common sense, don't install Python/VSCode twice if you already have it..  
  
- [Pico Setup Shell Script](https://github.com/raspberrypi/pico-setup/blob/master/pico_setup.sh)
- [Shawn Hymel Windows Pico SDK Install Guide](https://shawnhymel.com/2096/how-to-set-up-raspberry-pi-pico-c-c-toolchain-on-windows-with-vs-code/)
  
## Building a Project
A project should be started in its own directory, where the following are contained:
- All source code files
- CMakeLists.txt
- `pico_sdk_import.cmake`
  
Create a directory named `build` in the main project directory and enter the directory.  
On Linux open a terminal and run `cmake ..`  
On Windows open Git Bash in the terminal and run `cmake -G "MinGW Makefiles" ..`  
  
Next on either operating system run `make -j{4-16}`, where `{4-16}` is the maximum number of threads you wish to compile with. `-j4` or `-j8` are good defaults.  
  
The compile and link step will now proceed. If a syntax, linker, or other error are to occur they will happen at this step.  
  
Many issues are caused by a bad CMakeLists.txt file or on Windows not having a correct PATH setup.  
  

### Build Tips
- Any time a new library is added to a project it's highly likely you must add this to your CMakeLists.txt
- Any time the CMakeLists.txt is modified you must delete your `build` directory, recreate it, and run the appropriate `cmake` command again