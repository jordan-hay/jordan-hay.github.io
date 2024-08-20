---
layout: post
title:  "Running ARM Assembly Code on Raspberry Pi and Non-ARM System Google Colab"
date:   2024-8-20 06:25:17 -0800
categories: jekyll update technology
---

## A Step-by-Step Guide

When you're working with assembly language, the process of converting human-readable code into a machine-executable format requires a few important steps. This is especially true when dealing with different processor architectures, like ARM. In this guide, we'll walk through the process of assembling, linking, and running ARM assembly code on a non-ARM system using tools like GNU's assembler and linker, and QEMU for emulation.

### Understanding the Tools

Before we dive into the process, let's define some key terms and tools that we'll be using:

- **ARM (Advanced RISC Machine)**: ARM is a family of Reduced Instruction Set Computer (RISC) architectures that are known for their power efficiency and are widely used in mobile devices, embedded systems, and even servers.

- **GNU (GNU's Not Unix)**: The GNU Project is a free software initiative that provides tools like compilers, linkers, and debuggers. In our context, GNU refers to the toolchain that we'll use for compiling and linking ARM assembly code.

- **EABI (Embedded Application Binary Interface)**: EABI is a standard for how functions are called, how arguments are passed, how memory is managed, and how the binary code is formatted in embedded systems. It's designed for systems with limited resources, like those using ARM processors.

- **`gnueabi` (GNU Embedded Application Binary Interface)**: This term refers to the specific GNU toolchain and conventions that support ARM architectures using the EABI standard. It ensures that the generated binaries are compatible with ARM embedded systems.

- **QEMU (Quick Emulator)**: QEMU is an open-source software that allows for hardware virtualization and emulation. It can emulate different processor architectures, enabling you to run ARM binaries on a non-ARM system.

### Step 1: Preparing the Environment

The first step is to ensure that your environment is set up with the necessary tools to handle ARM assembly code. This involves updating your package lists and installing the ARM cross-compilation tools along with QEMU.

```bash
# Update package lists
!apt-get update -qq &> /dev/null

# Install ARM cross-compilation tools and QEMU
!apt-get install -y gcc-arm-linux-gnueabi binutils-arm-linux-gnueabi qemu-user qemu-system-arm &> /dev/null
```

- **`apt-get update`**: This command updates the list of available packages and their versions but doesn't install or upgrade any packages. The `-qq` option minimizes the output.
- **`gcc-arm-linux-gnueabi`**: This is the GNU Compiler Collection (GCC) for ARM architecture using the EABI standard.
- **`binutils-arm-linux-gnueabi`**: This package provides essential tools like the assembler and linker for ARM, following the `gnueabi` conventions.
- **`qemu-user`** and **`qemu-system-arm`**: These packages provide the QEMU emulator, allowing you to run ARM binaries on non-ARM systems.

### Step 2: Writing ARM Assembly Code in Google Colab

Next, we'll write a simple ARM assembly program that prints a message to the screen and then exits.

```assembly
%%writefile example.s
.global _start

.section .data
msg: .asciz "Hello from ARM!\n"

.section .text
_start:
    // Write "Hello from ARM!\n" to stdout
    mov r0, #1              // File descriptor 1 is stdout
    ldr r1, =msg            // Address of the message
    ldr r2, =15             // Length of the message
    mov r7, #4              // System call number for sys_write
    swi 0                   // Make the system call

    // Exit the program
    mov r7, #1              // System call number for sys_exit
    mov r0, #0              // Exit code 0
    swi 0                   // Make the system call
```

### Step 3: Assembling the Code in Google Colab

Once the assembly code is written, we need to convert it into machine code. This is done using the assembler from the `binutils-arm-linux-gnueabi` package.

```bash
# Assemble the code into an object file
!arm-linux-gnueabi-as -o example.o example.s
```

- **`arm-linux-gnueabi-as`**: This command invokes the assembler, converting the assembly source file (`example.s`) into an object file (`example.o`).
- **`-o example.o`**: Specifies the output file name for the object file.

### Step 4: Linking the Object File in Google Colab

The next step is to link the object file to produce an executable. This is where any unresolved addresses are fixed, and the code is prepared to run.

```bash
# Link the object file into an executable
!arm-linux-gnueabi-ld -o example example.o
```

- **`arm-linux-gnueabi-ld`**: This command invokes the linker, which takes the object file (`example.o`) and links it into an executable file (`example`).
- **`-o example`**: Specifies the output file name for the executable.

### Step 5: Running the ARM Executable in Google Colab

Finally, to run the ARM executable on a non-ARM system, we use QEMU.

```bash
!qemu-arm ./example
```

- **`qemu-arm`**: This command runs the ARM executable (`./example`) using QEMU's user-mode emulation.

### Conclusion

This guide has walked you through the process of setting up your environment, writing ARM assembly code, assembling and linking it, and finally running it on a non-ARM system using QEMU. By understanding each step and the tools involved—such as `gnueabi`, GCC, binutils, and QEMU—you can effectively work with ARM assembly code even if your development machine isn't natively running on ARM architecture.

## Appendix: Detailed Explanation of the ARM Assembly Code

This appendix provides a line-by-line breakdown of the ARM assembly code we used in the blog. The code is a simple program that prints "Hello from ARM!" to the screen and then exits. 

### The Assembly Code
```assembly
.global _start

.section .data
msg: .asciz "Hello from ARM!\n"

.section .text
_start:
    // Write "Hello from ARM!\n" to stdout
    mov r0, #1              // File descriptor 1 is stdout
    ldr r1, =msg            // Address of the message
    ldr r2, =15             // Length of the message
    mov r7, #4              // System call number for sys_write
    swi 0                   // Make the system call

    // Exit the program
    mov r7, #1              // System call number for sys_exit
    mov r0, #0              // Exit code 0
    swi 0                   // Make the system call
```

### Line-by-Line Explanation

#### 1. **`.global _start`**
```assembly
.global _start
```
- **Purpose**: Declares the `_start` symbol as global, making it accessible to the linker as the program's entry point.
- **Details**: This line ensures that the linker recognizes `_start` as the location where the program execution begins.

#### 2. **`.section .data`**
```assembly
.section .data
msg: .asciz "Hello from ARM!\n"
```
- **Purpose**: The `.data` section is used to store initialized data, like strings or variables.
- **Details**:
  - **`msg:`**: This defines a label `msg` that points to the memory location where the string is stored.
  - **`.asciz "Hello from ARM!\n"`**: This directive stores a null-terminated string (C-style string) in memory. The string is "Hello from ARM!\n", and `.asciz` ensures it is followed by a null byte (`\0`).

#### 3. **`.section .text`**
```assembly
.section .text
_start:
```
- **Purpose**: The `.text` section is where the actual code (executable instructions) is stored.
- **Details**: 
  - **`_start:`**: This label marks the beginning of the executable code. The `_start` label is defined here, which matches the entry point declared earlier with `.global _start`.

#### 4. **Write "Hello from ARM!" to stdout**
```assembly
mov r0, #1              // File descriptor 1 is stdout
ldr r1, =msg            // Address of the message
ldr r2, =15             // Length of the message
mov r7, #4              // System call number for sys_write
swi 0                   // Make the system call
```
This block of code prepares and executes a system call to write the message "Hello from ARM!" to the terminal.

- **`mov r0, #1`**: 
  - **Purpose**: Load the value `1` into register `r0`.
  - **Details**: The value `1` is the file descriptor for `stdout` (standard output). The `mov` instruction moves this value into `r0`, which will be passed as the first argument to the system call.

- **`ldr r1, =msg`**:
  - **Purpose**: Load the address of the message into register `r1`.
  - **Details**: The `ldr` (load register) instruction loads the address of the `msg` label (the string "Hello from ARM!\n") into `r1`, which will be passed as the second argument to the system call.

- **`ldr r2, =15`**:
  - **Purpose**: Load the length of the message into register `r2`.
  - **Details**: The length of "Hello from ARM!\n" is 15 characters, including the newline character. This value is loaded into `r2`, which will be passed as the third argument to the system call.

- **`mov r7, #4`**:
  - **Purpose**: Load the system call number for `sys_write` into register `r7`.
  - **Details**: The `sys_write` system call is identified by the number `4`. This is loaded into `r7`, which tells the kernel that the program wants to write data to a file (in this case, `stdout`).

- **`swi 0`**:
  - **Purpose**: Execute the system call.
  - **Details**: The `swi` (software interrupt) instruction triggers a system call. The value in `r7` determines which system call is made, and the values in `r0`, `r1`, and `r2` are passed as arguments.

#### 5. **Exit the Program**
```assembly
mov r7, #1              // System call number for sys_exit
mov r0, #0              // Exit code 0
swi 0                   // Make the system call
```
This block of code prepares and executes a system call to exit the program.

- **`mov r7, #1`**:
  - **Purpose**: Load the system call number for `sys_exit` into register `r7`.
  - **Details**: The `sys_exit` system call is identified by the number `1`. This value is loaded into `r7`, indicating that the program wishes to terminate.

- **`mov r0, #0`**:
  - **Purpose**: Load the exit code `0` into register `r0`.
  - **Details**: The value `0` indicates a successful termination of the program. This value is loaded into `r0` and passed to the `sys_exit` system call.

- **`swi 0`**:
  - **Purpose**: Execute the system call.
  - **Details**: As before, the `swi` instruction is used to trigger the system call, which in this case ends the program.

### Summary

This ARM assembly program demonstrates the basics of interacting with the operating system using system calls. It writes a message to the terminal and then exits, all while following the ARM EABI conventions. The program illustrates how to handle simple I/O and process control in ARM assembly, providing a foundation for more complex programs.

## Appendix: Bash Script for ARM Assembly on Raspberry Pi

This appendix provides a detailed explanation of a Bash script designed to create, assemble, link, and run an ARM assembly program on a Raspberry Pi. The script is intended to be executed directly in the Raspberry Pi terminal and demonstrates the entire workflow from writing assembly code to running the compiled program.

### Installation Requirements for ARM Assembly Development on Raspberry Pi

To develop and run ARM assembly code on a Raspberry Pi, you'll need to ensure that your system has the necessary tools and libraries installed. This section covers the installation requirements to get you up and running with ARM assembly programming on your Raspberry Pi.

#### Essential Tools for ARM Assembly Development

For assembling, linking, and executing ARM assembly code, the following tools are essential:

1. **GNU Assembler (`as`)**
   - **Purpose**: Converts ARM assembly code into machine code (object files).
   - **Installation**: Part of the `binutils` package.

2. **GNU Linker (`ld`)**
   - **Purpose**: Links object files to create executable binaries.
   - **Installation**: Also included in the `binutils` package.

3. **GNU Debugger (`gdb`)** (Optional)
   - **Purpose**: Useful for debugging assembly code.
   - **Installation**: Can be installed separately if needed.

### Installing the Necessary Tools

On a Raspberry Pi running a Debian-based distribution like Raspberry Pi OS, you can easily install these tools using the `apt` package manager. Here’s a step-by-step guide:

#### 1. **Update Package Lists**
   Before installing new software, it’s a good idea to update your package lists to ensure you’re getting the latest versions available from the repositories:
   ```bash
   sudo apt-get update
   ```

#### 2. **Install `binutils`**
   The `binutils` package includes the GNU assembler (`as`) and linker (`ld`), which are crucial for working with ARM assembly:
   ```bash
   sudo apt-get install binutils
   ```

#### 3. **Install `gcc`** (Optional)
   If you plan to work with mixed C and assembly code or need a compiler for C code, you should install the GNU Compiler Collection (`gcc`):
   ```bash
   sudo apt-get install gcc
   ```

#### 4. **Install `gdb`** (Optional)
   For debugging your assembly code, install the GNU Debugger (`gdb`):
   ```bash
   sudo apt-get install gdb
   ```

### Verifying Installation

After installation, you can verify that the tools are installed correctly by checking their versions:

- **Check GNU Assembler (`as`):**
  ```bash
  as --version
  ```

- **Check GNU Linker (`ld`):**
  ```bash
  ld --version
  ```

- **Check GNU Compiler Collection (`gcc`):**
  ```bash
  gcc --version
  ```

- **Check GNU Debugger (`gdb`):**
  ```bash
  gdb --version
  ```


### The Bash Script

```bash
# BASH Script for Raspberry Pi.
# Create the assembly code file
cat <<EOF > example.s
.global _start

.section .data
msg: .asciz "Hello, World!\n"

.section .text
_start:
    // Write "Hello, World!\n" to stdout
    mov x0, 1              // File descriptor 1 is stdout
    ldr x1, =msg           // Address of the message
    ldr x2, =15            // Length of the message
    mov x8, 64             // System call number for sys_write
    svc 0                  // Make the system call

    // Exit the program
    mov x8, 93             // System call number for sys_exit
    mov x0, 0              // Exit code 0
    svc 0                  // Make the system call
EOF

# Assemble the code
as -o example.o example.s

# Link the object file
ld -o example example.o

# Run the executable
./example
```

### Line-by-Line Breakdown

#### 1. **Creating the Assembly Code File**
```bash
# Create the assembly code file
cat <<EOF > example.s
```
- **Purpose**: This command creates a new file named `example.s` and writes the ARM assembly code into it.
- **Details**:
  - **`cat <<EOF > example.s`**: The `cat` command is used with a "Here Document" (denoted by `<<EOF`) to redirect a block of text into a file. Everything between `<<EOF` and `EOF` will be written to `example.s`.

#### 2. **Writing the Assembly Code**
```assembly
.global _start

.section .data
msg: .asciz "Hello, World!\n"

.section .text
_start:
    // Write "Hello, World!\n" to stdout
    mov x0, 1              // File descriptor 1 is stdout
    ldr x1, =msg           // Address of the message
    ldr x2, =15            // Length of the message
    mov x8, 64             // System call number for sys_write
    svc 0                  // Make the system call

    // Exit the program
    mov x8, 93             // System call number for sys_exit
    mov x0, 0              // Exit code 0
    svc 0                  // Make the system call
EOF
```
- **Purpose**: This block contains the ARM assembly code that will be written to the `example.s` file.
- **Details**:
  - **`.global _start`**: Marks `_start` as the entry point for the program.
  - **`.section .data`**: Begins a section for data storage, where the string "Hello, World!\n" is defined.
  - **`.asciz "Hello, World!\n"`**: Defines a null-terminated string in the data section.
  - **`.section .text`**: Begins the text section, where the executable code resides.
  - **`mov x0, 1`**: Sets up the file descriptor for `stdout` in register `x0`.
  - **`ldr x1, =msg`**: Loads the address of the message string into register `x1`.
  - **`ldr x2, =15`**: Loads the length of the message into register `x2`.
  - **`mov x8, 64`**: Sets the system call number for `sys_write` in register `x8`.
  - **`svc 0`**: Triggers the system call to write the message to `stdout`.
  - **`mov x8, 93`**: Sets the system call number for `sys_exit` in register `x8`.
  - **`mov x0, 0`**: Sets the exit code to `0` in register `x0`.
  - **`svc 0`**: Triggers the system call to exit the program.

#### 3. **Assembling the Code**
```bash
# Assemble the code
as -o example.o example.s
```
- **Purpose**: Converts the assembly code in `example.s` into machine code, stored in an object file named `example.o`.
- **Details**:
  - **`as`**: The GNU assembler for ARM, which assembles the source file into an object file.
  - **`-o example.o`**: Specifies that the output object file should be named `example.o`.

#### 4. **Linking the Object File**
```bash
# Link the object file
ld -o example example.o
```
- **Purpose**: Links the object file `example.o` to create an executable file named `example`.
- **Details**:
  - **`ld`**: The GNU linker for ARM, which links object files and resolves addresses to produce an executable.
  - **`-o example`**: Specifies that the output file should be named `example`.

#### 5. **Running the Executable**
```bash
# Run the executable
./example
```
- **Purpose**: Executes the ARM binary `example`.
- **Details**:
  - **`./example`**: Runs the `example` file from the current directory.

### Summary

This Bash script automates the process of writing, assembling, linking, and executing ARM assembly code on a Raspberry Pi. It uses standard tools provided in the GNU toolchain (`as` and `ld`) to convert human-readable assembly code into a machine-executable format. The script is particularly useful for quickly testing ARM assembly programs directly on the Raspberry Pi, a platform widely used for embedded systems and educational purposes. By understanding each step, you can modify and extend the script to handle more complex assembly projects.