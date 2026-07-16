# OS

[← Back to README](../README.md)

## Why we need computer?

Human hardware is so insufficient and slow. 

Human being are so weak in computing and memory. For example, if we need to calculate `199 X 577`, we need at least 30 second to solve, but for computer, it only takes 3ms.

## Why computer has to be binary?

Cause it is the reliable way to run computation by electricity in physics. 

Of cause, there is computer using Ternary, but it is unstable. 

The hardware is reliable on billions of transistors
- Current is on, means 1
- Current is off, means 0

## What's license?
A legal document, the declaration of the ownership. 

It's a permission slip, the set of rules created by the owner. 

## What is image?
A blueprint / snapshot of how to organize massive 1 and 0 on hard drive. 

Specifically when copy large files from one device to another. 

## Difference between Mac User folder & Macintosh HD?
Macintosh HD is your whole computer physical hard drive. Everything that stores in your laptop. 

User folder (like Sam Chan), it’s personal user home folder. If Macintosh HD is whole apartment building, then personal home folder is like a single apartment. 



## What is this project about? Find most of resource in wiki.osdev.org
Development of unix-like kernel. A tiny hobby operating system for x86 PCs, that boosts from 512-byte real-mode loader, uses BIOS INT 13h to fetch the next sector, then hands off a simple 32-bit multitasking kernel you write in C and assembly. After that, the control jumps  into protected mode, where paging, multitasking, FAT16, small heap, ELF loading, and keyboard input. Development of real mode & protected mode. 

## Key components	

1. Bootloader (512B)
2. Mode switch
3. Paging + virtual memory
4. Kernel heap (malloc free)
5. Task scheduler
6. Virtual file system (VFS)
7. FAT16 driver 
8. ELF loader 
9. Keyboard driver
10. Shell

The mini-OS starts with 512-byte real-mode boot block, then switches the CPU into 32-bit protected mode, where a small kernel handle memory, tasks, files and user commands. 


## Component In plain words
1	Bootloader	First code the BIOS loads (512 bytes at 0x7C00). It prints “Hello World!” and pulls the rest of the kernel from disk.
2	Mode switch (GDT)	Sets up a table, flips a CPU bit, and moves from 16‑bit “real mode” to 32‑bit “protected mode” so you can use more memory and safety checks. 
3	Paging / virtual memory	Gives every process its own fake address space by mapping virtual addresses to real RAM pages, stopping apps from stepping on each other. 
4	Kernel heap (malloc/free)	A tiny bookkeeper that remembers which RAM blocks are free or taken, so the kernel and drivers can grab memory on demand.
5	Task scheduler	Saves CPU registers, picks the next ready task, and performs a context switch so many programs can appear to run at once. 
6	Virtual File System (VFS)	One common doorway for all storage types; lets code call “open/read/write” without caring if the data is on FAT, RAM‑disk, or something else. 
7	FAT16 driver	Walks the cluster chain table to find, read or extend files stored on a FAT16‑formatted disk. 
8	ELF loader	Reads the headers in an ELF executable, maps its sections into memory, and jumps to the program’s entry point so user apps can start. 
9	Keyboard driver	Catches the keyboard interrupt, translates scancodes to characters, and hands them to the shell.
10	Shell	A text‑based command interface that lets users type commands which the kernel then runs; same idea as Bash or PowerShell.


## X86
AS intel chip nickname for chip series ended in“86” (8086, 80286, …), each chip has 16-bit registers, right after with 32-bit, and right now is 64-bits, like“x86-64”. A CPU has the pre-set operation (like addition, subtraction,…), in terms of CPU design, the circuits is to execute those operations. It is the field of processor design. CPU Register is a location where to store the ready-load data for RAM. There are 5 main components in CPU design, arithmetic logic unit (ALU) 算数逻辑单元，control unit(CU), memory unit, registers, clock. 

## OS
Once the boot loader has configured system, and located the OS kernel, it will transfer the control to OS. The M1 Mac is using Apple M1 chip, and its ARM framework, which’s different from x86 by instructions set architecture(ISA). (Those commands computer’s CPU can understand and execute) 

## What is unix-like OS?
The OS acts like classic UNIX, but built from different code. Same user command-line tool, has implemented POSIX API that can write C to compile. (Linux, MacOS, BSD family-FreeBSD OpenBSD, …). The core of Unix OS is called Unix Kernel, which’s written by C language.

## BIOS
BIOS stands for Basic Input/Output System, When you power on your computer, BIOS is a firmware, which will initialize hardware, and wait for bootable device(hard drive, SSD, …). It’s the first program to run after power on, initialize hardware, and running operating system. 

## Bootlader
It’s a program, its job is to set up the necessary environment to execute the operating system kernel.

## Build from scratch
Means build program from blank file or simple framework.

## RAM
RAM is a short-term memory that stored in computer, meanwhile, ROM stands for read-only memory, the non-volatile memory. The difference is the data in RAM will disappear after power off, and ROM will NOT. (Like BIOS). 


## What is Kernel?
Kernel acts as the core of operating system, the OS.  It’s the intermediary between kinds of hardwares, and software applications. You can simple consider computer is combined with three components, application on top, Kernel on middle, and hardware(CPU, hard disk, keyboard…) at bottom. 

## Interface
There are two types of interface in computer, one is user interface (cursor, desktop, bin…on the screen), the other is command-line interface (terminal, literally can do anything like Windows by typing text command).



## How to run Linux by VM
To use Disk Image File (ISO file), it is the instruction / blueprint about running operating system on virtual environments. Ubuntu is an open source OS based on Linux. 



## Real Mode set up (boot-loader for x86 in assembly)
What is Real Mode? It is the initial mode of x86 CPU, when computer is powered on. 

## What will the boot-loader do?
1. Run the Real Mode
2. Prepare the system
3. Transitioning to Protected Mode
4. Load the kernel


## Memory
Boot loader is a small program responsible for loading the OS into RAM, while power on. Once you power on, the BIOS will find the boot loader, and it the loader will start to set up process(like memory segments). 

Memory segmentation is a management technique to put primary memory into segments or sections, the descriptor will break the process into small part, which called segments. And GDT (global descriptor table) is a data structure to hold the memory, each entry is a ‘Descriptor’, and multiple descriptor becomes ‘Table’. 

GDT is used by CPU to obtain all information, and located in RAM. It stores the memory segments (including address, size, access permissions). Also, there is LDT (local Descriptor Table) as well. the local one is for specific process, while the global one for other memory segment. And for IVT (Interrupt vector table) is a data structure, for CPU to decide which program execute first when interrupt signal received. 




## Transitioning to protected mode(32-bit mode)
Because, in real mode, there is limitation of 16-bit registers, 1 MB memory, so boot loader will transition the CPU into protected mode. The boot loader will switch the CPU into Protected Mode, after that load the OS kernel into RAM. RAM is a workspace for both boot loader and OS Kernel. 

Protected mode, it’s also called protected virtual memory mode, specially for x86 architecture. It uses for system security, and enable features(like multitasking, virtual memory…). Sometimes, when you use the address of descriptor and actual start memory is not right next to (maybe it’s 8 bytes further than starting address), so you need to‘MOV’the descriptor to target memory location to get start the program, that’s we called‘Offset’, or‘Segment Offset’ （移量）. 

Also, the reason why we start at ‘0x7c00’, is because it’s the early standard convention established in x86 architecture. 

Once our own system started, the BIOS runs in Real Mode (16-bit), and will load the Boot Loader from the hard disk to the RAM. Our boot.asm is an assembly code file, to be assembled Into binary file (boot.bin). 

When you power on, the CPU will initialize by BIOS from Real Mode, for unleashing your CPU power, you can use 32-bit address in protected mode, which is the fundamental feature of x86 architecture. 0x7c00 is the standard location, where tells the BIOS start to load the boot loader. 

We use QEMU as the emulator and virtualizer in virtual environment (virtual memory). QEMU is the emulator of hardware environment (includes BIOS). BIOS is a firmware embedded in the hardware. That’s why we use the command ‘qemu-system-x86_64 -hda ./boot.bin’, to boot from specific image. And also, QEMU integrated the tool like GDB, to debug your kernel and boot-loader.



## Enable the A20 line / Setting up the GDT
While the boot loader start the protected mode, because the 8086 architecture (x86 is an extension) only have 20 bits address bus, meaning has line A0 - A19, 1 MB = 2*20 bytes, A20 refers to the 21st address line on processor’s bus.  （In computer architecture, the bus means the highway for transferring data between each components 总线）

Layout asm, is a command in GDB tool to debug the low-level code. 



## Gcc cross compiler
To use C to create our own OS, and gcc is targeted for linux, that’s why to create Cross Compiler
To build this compiler, so that can code in bare-metal environment, which is application run directly on hardware. When you have the compiler, you don’t have library, need to write everything for yourself. 



## How compilation works in C?
There are 4 steps: (in the example of C)
Preprocessor, put the source code file into text file (hello.c - hello.i)
Compiler, translate text file into assembly (hello.i - hello.s)
Assembler, translate assembly into machine-language instruction, packages into relocatable object file (hello.s - hello.o)
Linker, merge object file with target library (hello.o - hello)



## Loading 32-bit kernel into memory
The kernel is the core of your operating system, it needs to be loaded into your memory.

When we do compile, we have to call the make file to call the build.sh, for pre-setting up correctly. 

We need tell the kernel to run the location, and we jump to that location. 
The linker script is to control how the binary file is working in the memory.

To clean the object file: In the makefile ‘clean’ keyword, to run ‘make clean’ to clean all the created files (object, bin file) after running ‘./build.sh’

In this stage, the kernel.asm, is the assembly code to transitioning from real mode, to protected mode. The command ‘MOV DS’ (includes es, fs, gs…), is the memory segment register. And after that, ‘call kernel_main’ to transfer control from assembly to C language. 



## Why we need to use QEMU and GDB to debug?
QEMU emulates the PC hardware in software, GDB (remote) hooks into QEMU’s built-in GDB stub, letting you set breakpoints, single-step instructions, inspect registers and memory, and load symbol information from your compiled kernel



## The alignment problem
Data being placed in memory address, need to meed the specific alignment requirement. The boot-loader maybe except the binary to be specific size for 512 bytes, but the data only has 300 bytes, so it needs to make the rest of data memory into 0, to become 512 bytes. 



Setting up the IDT (Interrupt Descriptor Table) in kernel
It is a data structure in low-level OS, to handle interruption and exception. 

Search for IDT entry point to define all the name in table. 




## Implement IO function

PIC(Programmable interrupt controller), you can think it as the ‘traffic police’ between hardware and CPU. When the hardware has the IRQ (interrupt request), 

There is IRQ number for each interruption. One is for master, Master PIC handles IRQs 0–7,  the other is slave, Slave PIC handles IRQs 8–15 and connects to the master on IRQ2,  two separate controller.



## Heap implementation
32‑bit Addressing: CPU registers are 32 bits, so maximum directly addressable RAM is 4 GB.
Heap Purpose: A contiguous region in virtual memory used for dynamic allocations (e.g., kernel objects, buffers).



## Paging
When a computer runs a program, it needs a space of memory to run the program. Each program will be assigned by each logical memory space. And logical memory is part of virtual memory. 

Virtual memory means the memory is not pointing to the address as the value told, it can be moved, can resize. Computer will segment your memory into one section (page). Paging works in 4096 byte block size by default, and this block is called pages. Llike 5% for OS, 5% for web browser. This proportion of memory (5%) is called segmented memory. 

Once the program is being loaded, the logical memory will point to the page table, and page table will decide which segment of memory is being pointed to the physical memory. The physical memory means the memory that is pointing to the same memory as the value told. It cannot be moved (AKA. It is the RAM). So the page table will optimize which memory segment is doing best for computer. 

When there is not enough space for RAM, the OS will move the segment of memory to SSD (disk), it called paging out / swapping. Because too much segment makes the RAM running so slow. 

Google ‘osdev paging’



## Debugging the OS with QEMU and GDB

During Lesson 39, the kernel binary (os.bin) is launched under QEMU and paused immediately for debugging:

qemu-system-i386 -hda ./os.bin -S -gdb stdio

* -S halts the CPU at startup, waiting for a debugger connection.
* -gdb stdio binds the GDB stub to the console.

In Lesson 40, you run the OS without a debugger to verify functionality:

qemu-system-i386 -hda ./os.bin

Tip: If the emulated display flashes, it often indicates the kernel crashed or entered an infinite loop. You can reconnect GDB or add logging to pinpoint the fault.


## Basics of the FAT16 File System
FAT16 is an older Microsoft file system that organizes disk data into:
* Boot Sector: Contains filesystem metadata (e.g., bytes per sector, sectors per cluster).
* Reserved Sectors: Space reserved for the bootloader and other structures.
* File Allocation Table (FAT): A table mapping each cluster to the next cluster in a file or marked as end-of-file.
* Root Directory: A fixed-size table of directory entries at the start of the data area.
* Data Area: Actual file and directory contents, divided into clusters.

Each directory entry includes attributes (e.g., read-only, hidden) and metadata (filename, size, starting cluster). In C structures, use __attribute__((packed)) to ensure the compiler does not insert padding, matching on-disk layouts.



## Mounting a FAT16 Disk Image in Linux
To inspect and work with os.bin as a FAT16 volume:

sudo mkdir /mnt/d
sudo mount -t vfat ./os.bin /mnt/d

* -t vfat tells the kernel to use the FAT16/32 driver.
* After mounting, files become accessible under /mnt/d.
You can use Bless (a GTK hex editor) or hexdump to inspect the boot sector and verify filesystem parameters.


## The Virtual File System (VFS) Layer
The VFS abstracts multiple file system implementations behind a uniform interface. When a user program calls fopen(), the VFS:
1. Parses the file path.
2. Determines which registered filesystem (e.g., FAT16, ext4) handles that path.
3. Forwards the open/read/write calls to the appropriate filesystem driver.

This design lets the kernel support many filesystems without changing user-space code. All filesystem drivers implement the same set of VFS operations (open, read, write, close, etc.).



Implement the FAT16, there is manual, the Microsoft FAT32 Spec(SDA contribution)

Up to 51 section, but as long as the code is right, there is debug in building. 


## Use kernel.c to debug

- [ ] Debug on fat16 open function 52, 54:59
- [ ] Debug, section 54, 6:46
- [ ] Debug, section 58 3:32
- [ ] Debug, section 60, 2:02 close the file
- [ ] Debug, section 70, 8:11 first program run on it
- [ ] Debug, section 77, calling the firs kernel land, 1:54, the whole section is running and debug
- [ ] Debug, section 79, reading the task from stack, from 17:16
- [ ] Debug, section 80, create point command in kernel , from 10:51
- [ ] Debug, section 84, interrupt handle, from 17:55
- [ ] Debug, section 87, keyboard driver, from 8:47
- [ ] Debug, section 88, from 8:08
- [ ] Debug, section 89, from 4:53
- [ ] Debug, section 95, from 2:27, after install the dump bet for blank.elf
- [ ] Debug, section 97, from 22:56, the elf loader
- [ ] Debug, section 99, from 12:28, user C program
- [ ] debug, section 102, from 19:54, implement malloc
- [ ] Debug, section f 109, from 6:00, create a shell



逆向思维去 debug 结果 output 导向




## kennel panic
It’s the panic function, it will print the message to screen, and hold the kernel. 


## User land
user land is when the processor is in ring3.

Restrictions of user land, 

Setting up the TSS (task switch segment) to get used. 
We need to pretend we back from interrupt, to call the “iret”, 

TSS example structure, 



## kernel land
When the processor is in its maximum privileged state.



Kernel from user land  / how task is worked with kernel 

The code to print from user land. 

Lots of using the push keyword in asm file. 


## Calling the kernel overview
* Some overview, the processor pushes the same information as we pushed to get into the user land in the first place to the stack. 
* The C interrupt hander for 0x80 is called.
* The kernel does the action that it was instructed to do from the user land. 
* Execution continues after the user lands “init 0x80” instruction
* The EAX register is populated with the return result from the kernel.


There is ISR80H handle command function.

Accessing the task from stack. 


Keyboard access in protected mode

Keyboard buffer will be inside the process structure, tail and head as variable will help push and pop our keyboard buffer

The keyboard buffer, the tail and head both is 0, both points to index 1 at the first place, and changing the buffer where both points to. 

Index  = tail % 1024, the solution is to use the modules operator. 

We must parse the scan code. The PIC won’t tell us which one is parsed. 

Have the keyboard virtual layer.



## Keyboard development

PS/2 keyboard, we have to implement the port of the PS/2. 

There is scan code set 1 table. 



## ELF file
- [ ] Elf file are objects files that contain symbol’s that point to data or functions. Without them, we can only load binary file. 
- [ ] Object file can be linked to produce an executable elf file that can be loaded by the kernel. 
- [ ] Elf file can be linked through the runtime. 
- [ ] Q: Why we need the elf files?
- [ ] Two .o file, and one .so file, to become .elf file by linker.
- [ ] The layout of elf format, 
- [ ] The c structure of elf header
- [ ] The string table of elf file
- [ ] The program header, section header, 
- [ ] More reference is in the searching keyword, elf file specification pdf.
￼


## To read the elf file, the function or address, use this command
readelf -a ./blank.elf