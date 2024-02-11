# Mechatronics_ECE_Ecosystem
Center for anything that makes lights blink and motors spin.
  
The new revision of a cohesive electrical system to support all Mechatronics projects consisting of several "modules" communicating on shared multi-drop buses. 
Each module consists of:
- Hardware (schematic + PCB)
- Firmware and Build Files
- Fabrication files
  
Each module shall:
- Have a specific and well scoped goal
- Serve to more efficiently distribute processing as a part of the whole system
- Respect the shared communications standards defined in this repository
- Be well researched, tested, and documented

## Repository Structure
- Embedded CAN Bus
    - Contains documentation and libraries for inter-module communications

- Board Support
    - List of supported hardware
    - Contains information on supported MCU/FPGAs
    - Example projects and guides on how to use and implement a specific device

- General Documentation
    - well... it's in the name
    - Overall architectural goals and descriptions of our target system and all current/future needs

- KiCad Libraries
    - KiCad 7 symbols, footprints, and models created for individual modules

## General Hardware Support
A set of selected processors and FPGAs are listed that contain the requisite information to quickly bring any project up. These parts are by no means the only acceptable options, but are provided to reduce the load when starting a project.
  


Also run linux, it makes all of this so much easier. :)