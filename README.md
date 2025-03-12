# Getting started to program with SDL in C

- [Getting started to program with SDL in C](#getting-started-to-program-with-sdl-in-c)
  - [Installing SDL2 Libraries](#installing-sdl2-libraries)
    - [SDL2 on Ubuntu Linux](#sdl2-on-ubuntu-linux)
    - [SDL2 on Macos](#sdl2-on-macos)
    - [SDL2 on Windows](#sdl2-on-windows)
  - [Installing SDL3 Libraries](#installing-sdl3-libraries)
    - [SDL3 on Ubuntu Linux](#sdl3-on-ubuntu-linux)
    - [SDL3 on Macos](#sdl3-on-macos)
    - [SDL3 on Windows](#sdl3-on-windows)
  - [Running the sdl hello program](#running-the-sdl-hello-program)
  - [Bonus](#bonus)

This is a simple tutorial to install and run a simple program which uses the _Simple Direct Media Library (SDL)_ in a C program.

This tutorial assumes that you have installed and are familiar with running a C program as shown in the tutorial [here](https://github.com/Makerspace-KTH/c_programing_intro)

To summarize, the tutorial assumes that:

1. you are using either Windows (10 or 11), Ubuntu Linux, or Macos.
2. You have installed GNU C compiler (GCC) using the method described in the tutorial for your operating system. 
3. You are able able to successfully compile the a program using make.

A program with SDL libraries will not only require you to include and call the functions in the SDL library but also to provide the runtime libraries during the _linking_ process. The following sections describe how to install a SDL library (2 or 3) and to tell the compiler to use it and link your program against it, to create the executable that can be run on your machine.

## Installing SDL2 Libraries
SDL contains various libraries based on what type of functions are called. For example, the _SDL2\_mixer_ library contains functions to manage sound when creating games, while _SDL2\_ttf_ library helps in creating fonts. The libraries are separated based on their functions but also to ensure that only the required parts of the libraries are used for building the executable. The size of the library will have a influence on the size of the executable cerated.

### SDL2 on Ubuntu Linux

On Ubuntu linux, use the following command in the terminal to install the required libraries:

    $ sudo apt install -y libsdl2-2.0-0 libsdl2-image-2.0-0 libsdl2-mixer-2.0-0 libsdl2-ttf-2.0-0 libsdl2-net-2.0-0 libsdl2-dev libsdl2-image-dev libsdl2-ttf-dev libsdl2-net-dev libsdl2-mixer-dev
  
### SDL2 on Macos

On mac with _homebrew_ installed please use the following command in terminal to install the libraries:

    $ brew install sdl2 sdl2_mixer sdl2_image sdl2_ttf sdl2_net


### SDL2 on Windows

On widows with Msys2, please open the msys2 console and issue the following commands to install the SDL2 libraries.

    $ pacman -S mingw64/mingw-w64-x86_64-SDL2 mingw64/mingw-w64-x86_64-SDL2_image mingw64/mingw-w64-x86_64-SDL2_ttf mingw64/mingw-w64-x86_64-SDL2_mixer mingw64/mingw-w64-x86_64-SDL2_net

Answer _Y_ to proceed with the installation.


## Installing SDL3 Libraries
SDL contains various libraries based on what type of functions are called. For example, the _SDL2\_mixer_ library contains functions to manage sound when creating games, while _SDL2\_ttf_ library helps in creating fonts. The libraries are separated based on their functions but also to ensure that only the required parts of the libraries are used for building the executable. The size of the library will have a influence on the size of the executable cerated.

IMPORTANT  
SDL3 is a very new release. As a result, for Ubuntu Linux all will be built from source, and for Windows and Mac libraries like SDL_mixer and SDL_net need to be built from source.

### SDL3 on Ubuntu Linux

SDL3 is a very new release and has still not entered into package management in Ubuntu Linux. It will be installed by compiling the same. 

On Ubuntu linux, use the following command in the terminal to install the required libraries:

#### 1. Install CMake
    $ sudo apt-get update
    $ sudo apt-get install build-essential
    $ sudo apt-get install cmake
    

#### 2. Download SDL3 from here: [SDL3-3.2.8.tar.gz](https://github.com/libsdl-org/SDL/releases/download/release-3.2.8/SDL3-3.2.8.tar.gz)

#### 3. Extract the archive and compile
Open a terminal and go to Downloads folder
    $ cd ~/Downloads

Extract the downloaded file.
    $ tar -xf SDL3-3.2.4.tar.gz

 Go to the extracted archive : for example I have the archive in the downloads directory : 
    $ cd ~/Downloads/SDL3-3.2.4 

#### 4. Compile SDL3 and install
Issue the following commands:

```bash
mkdir build
cd build
ccmake ..
type c for configure
type c again
type g for generate
make
sudo make install
```
This will install _sdl3_ into the standard library on your distribution.

### SDL3 on Macos

On mac with _homebrew_ installed please use the below command in terminal to install the libraries. Other libraries like SDL3_mixer and SDL3_net need to be built from source.

    $ brew install sdl3 sdl3_image sdl3_ttf

#### SDL3 libraries from source on Macos

Download the zip-file for the SDL library via the green 'code' button on GitHub. For example, you'll find the latest release for SDL_net here: https://github.com/libsdl-org/SDL_net.

Extract the zip-file.

Open your terminal and with _homebrew_ install cmake:

    $ brew install cmake

In your terminal, navigate _into_ the newly downloaded SDL directory.

Run below commands to build (note that you have to choose between arm64 and x86_64):

    $ cmake -S . -B build \
    -DCMAKE_INSTALL_PREFIX=/opt/homebrew \
    -DCMAKE_BUILD_TYPE=Release \
    -DCMAKE_INSTALL_NAME_DIR=/opt/homebrew/lib \
    -DCMAKE_OSX_ARCHITECTURES="arm64;x86_64"

    $ cmake --build build

    $ cmake --install build

Now, you should hopefully be able to include and link the new library in the same way as your directly installed SDL packages.

### SDL3 on Windows

On windows with Msys2, please open the msys2 console and issue the below commands to install the libraries. Other libraries like SDL3_mixer and SDL3_net need to be built from source.

    $ pacman -S mingw64/mingw-w64-x86_64-SDL3 mingw64/mingw-w64-x86_64-SDL3-image mingw64/mingw-w64-x86_64-SDL3-ttf

Answer _Y_ to proceed with the installation.

#### SDL3 libraries from source on Windows

Download the zip-file for the SDL library via the green 'code' button on GitHub. For example, you'll find the latest release for SDL_net here: https://github.com/libsdl-org/SDL_net.

Extract the zip-file and place it somewhere accessible, like in the msys64/home/user directory.

Open the msys2 console and install cmake.

    $ pacman -S mingw-w64-x86_64-cmake

With the msys2 console, navigate _into_ the newly added SDL directory.

Run below commands to build.

    $ cmake -S . -B . -DCMAKE_INSTALL_PREFIX=/mingw64
    $ cmake --build . --config Release
    $ cmake --install . --prefix /mingw64

Now, you should hopefully be able to include and link the new library in the same way as your pacman installed SDL packages.

## Running the sdl hello program

In order to run the hello program using Makefile, rename the right makefile for you system. For example, on a Windows computer, rename _Makefile\_win_ to _Makefile_. 

Ensure the Makefile have the correct active lines of code for your version of SDL (2 or 3). 

Open a terminal and point the working directory to the project folder. Refer to the [_c\_programming\_intro_](https://github.com/Makerspace-KTH/c_programing_intro#4-launch-and-run-a-c-program) for details for your operating system.

Run the makefile based on your OS to build the _hello_ executable

Windows:

    $ mingw32-make.exe

Linux / macos:

    $ make

Execute the binary _hello_

    $ ./hello 

or

    $ ./hello.exe

Expected output:

![Expected Output](contents/expected-output.png?raw=true "Expected output")

Run

$ make clean

to remove the binaries.

## Bonus

Try to download and compile a full alien game from [here](https://github.com/Makerspace-KTH/alien).
