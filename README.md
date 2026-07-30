# GB-Emu

A Game Boy emulator written in C.

## Features
- **CPU Emulation**: Accurate emulation of the Sharp LR35902 Game Boy CPU.
- **PPU Emulation**: Graphics rendering including backgrounds, sprites, and LCD interrupts.
- **Memory Management**: Support for Game Boy cartridge loading and basic memory banking.
- **Timer and DMA**: Accurate timer ticking and Direct Memory Access (DMA) transfers.
- **Input Support**: Gamepad and keyboard input mapped through SDL2.
- **Multi-threaded Architecture**: Separates the main CPU emulation loop from the UI and event-handling loop using POSIX threads.

## Drawbacks
- **No Audio**: The Audio Processing Unit (APU) is not currently implemented. (*A win for the no sounds gaming gang*)
- **Platform Limitations**: Relies on POSIX specific headers (`pthread.h`, `unistd.h`), meaning it primarily targets **Linux**. Native Windows compilation requires additional work *which I am too lazy at the moment to do*.
- **Basic UI**: Lacks advanced quality-of-life features such as save states, rewinding, or a built-in graphical ROM picker. (*Who even needs these features anyways ? Just finish the game in one sitting without saving*)
- **Original DMG Only**: No support for Game Boy Color (GBC) ROMs. (*It is called a "GB-Emu" and not a "GBC-Emu"*)

## Build Environment Setup

This project uses `CMake` and requires `SDL2` libraries. The instructions below are for Linux systems.

### Prerequisites
Install the required development packages:
```bash
# for Debian based distributions
sudo apt update
sudo apt install build-essential cmake libsdl2-dev libsdl2-ttf-dev
```
```bash
# for Arch based distributions (I use Arch, btw.)
sudo pacman -S base-devel cmake sdl2 sdl2_ttf
```
```bash
# for Fedora based distributions
sudo dnf install gcc make cmake SDL2-devel SDL2_ttf-devel
```

### Building the Project
From the root of the project directory, run the following commands to create a build directory and compile the emulator:
```bash
mkdir build
cd build
cmake ..
make
```

## How to Run

The emulator runs from the command line and takes the path to a ROM file as its argument.

Assuming you have a directory named `roms` in the root of the project containing a ROM named `rom.gb`, you can run the emulator from the `build` directory like this:

```bash
./gbemu/gbemu ../roms/rom.gb
```
*(Note: Since CMake builds the executable inside `build/gbemu/`, you invoke it with the relative path to your ROM).*
