# Computers

## Overview

### Input

The computer receives data and instructions from various input devices, such as a keyboard, mouse, microphone, or sensors. This input can be in the form of text, numbers, images, sound, or other types of data.

### CPU

The central processing unit (CPU) is the brain of the computer. It interprets and executes instructions stored in the computer's memory. The CPU performs tasks such as calculations, data manipulation, and control of other hardware components.

### Memory

Computers have various types of memory, including RAM (Random Access Memory) and storage devices like hard drives or solid-state drives. RAM is used for temporarily storing data and program instructions that the CPU needs to access quickly. Storage devices hold data and programs even when the computer is powered off.

### Output

After processing the input data and executing instructions, the computer generates output. Output can be displayed on a screen, printed on paper, played through speakers, or sent to other devices. The output is the result of the computer's operations and can be in various forms, such as text, images, sound, or video.

### Control

The computer's operating system manages the overall operation of the computer, including managing hardware resources, running and switching between software programs, and handling user interactions. It also ensures that tasks are executed in a coordinated manner.

### Storage

Data and software programs are stored on various storage devices, such as hard drives, solid-state drives, optical discs, or cloud-based storage. These devices provide long-term storage for information even when the computer is turned off.

### Communication

Computers can communicate with other devices and networks, allowing them to access the internet, share data, and interact with other computers. This communication can be wired (e.g., Ethernet) or wireless (e.g., Wi-Fi or Bluetooth).

### Peripherals

Peripherals are additional devices that can be connected to the computer, such as printers, scanners, external hard drives, and webcams. These devices extend the computer's functionality and allow it to interact with the physical world.

### Software

Software is a crucial component of a computer's operation. It includes the operating system, which manages hardware resources and runs applications, as well as applications and programs that perform specific tasks, such as word processing, web browsing, and gaming.

### Hardware

The physical components of a computer, such as the CPU, memory, motherboard, graphics card, and input/output devices, make up the computer's hardware. These components work together to enable the computer to process data and perform tasks.

## Boot Process

Power-On Self Test -> BIOS init (firmware that inits hardware) -> BIOS loads boot loader into memory -> boot loader loads OS into memory -> OS kernel takes control and inits services, drivers etc, -> user presented with gui

1. **Power-On Self-Test (POST):** The hardware components of the computer perform a Power-On Self-Test (POST) to check that essential hardware is functioning correctly.

1. **BIOS/UEFI Initialization:** The BIOS (or UEFI) firmware initializes hardware components, including the CPU, memory, storage devices, and input/output devices.

1. **Boot Device Selection:** The BIOS/UEFI firmware selects a boot device based on the configured boot order (e.g., internal hard drive, USB drive, CD/DVD drive, network).

1. **Loading the Boot Loader:** The BIOS/UEFI firmware loads the first sector of the selected boot device into memory. This sector contains the boot loader.

1. **Execution of Boot Loader:** The boot loader program is executed. Its main task is to locate and load the main part of the operating system, often stored in a separate partition or file.

1. **Loading the OS Kernel:** The boot loader loads the OS kernel into memory. The kernel is the core of the operating system, responsible for managing hardware resources and initializing key components.

1. **Operating System Initialization:** The OS kernel takes control of the system and starts initializing system services, device drivers, and other components necessary for the operating system to operate.

1. **User Interface (GUI):** Depending on the OS configuration, the user may be presented with a login screen or graphical user interface (GUI) as the OS completes its startup process. This step may also include the loading of user-specific settings and preferences.

## Operating System

Manages and controls the computer's hardware and provides a platform for other software applications to run. The operating system acts as an intermediary between the hardware and software, facilitating the execution of various tasks and ensuring that resources are allocated efficiently.


1. **Hardware Abstraction:** The OS abstracts the complex hardware details, providing a simplified interface for applications. This abstraction allows software to be written without needing to understand the intricacies of hardware components.

1. **Resource Management:** The OS manages system resources, including CPU time, memory allocation, input/output devices, and network connections, ensuring that multiple software programs can run concurrently without conflicts.

1. **Process and Task Management:** The OS controls the execution of processes and tasks, scheduling them to run on the CPU and managing their lifecycle, including creation, suspension, and termination.

1. **File System Management:** It provides a file system that organizes and stores data on storage devices, allowing applications to read, write, and manage files.

1. **User Interface:** Many operating systems include graphical user interfaces (GUIs) that provide a user-friendly way to interact with the computer, including windows, icons, menus, and mouse support.

1. **Security and Access Control:** The OS enforces security policies and controls access to resources, ensuring that only authorized users and programs can perform certain actions.

1. **Networking:** It provides networking capabilities, allowing computers to communicate with each other over networks and access the internet.

1. **Error Handling:** The OS manages errors and exceptions, preventing crashes and providing error messages or logs when issues occur.

1. **Device Drivers:** It includes device drivers that enable communication between the operating system and hardware devices, ensuring compatibility and functionality.

1. **Updates and Maintenance:** Operating systems can receive updates and patches to improve functionality, security, and stability.

