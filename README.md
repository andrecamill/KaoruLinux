# **KaoruLinux 🌸**

A minimal, bare-bones Linux distribution environment featuring **BusyBox**, **musl libc**, and the **Tiny C Compiler (TCC)**.

KaoruLinux is meant to be a simple Linux distribution made to learn how to easily build something from scratch starting from the Linux kernel.
KaoruLinux features upstream Linux kernel, standard C library musl and TinyCC, a small C compiler.

**Required Setup**

Kernel and BusyBox compilation are required.

### **Prerequisites & Kernel Compilation**

Clone the repository and initialize the submodules.
It is raccomended to use the flag `--depth=1` when cloning submodules to save space by only cloning last commit of every submodule repo.

#### Clone submodules 
`git submodule update --init --depth=1`

#### Compile the Linux Kernel  
`cd linux/`  
`make -j$(nproc)`  

Kernel image will be built in arch/x86/boot/bzImage (for x86\_64)  

### **BusyBox Setup**

BusyBox provides the core userland utilities.

In order to correctly compile BusyBox, enter menuconfig with `make menuconfig` and flag the `Build static binary (no shared lib)` box.
This is required as I still not (correctly) implemented shared libraries. 

After configuration is done, run `make -j$(nproc)`

**Build Instructions**

Run `genall`

**Testing**

You can easily test your build using QEMU emulator

```bash
make qemu
```

**Warnings**

You can remove the generated "linuxrc" file.
As of right now, any userspace utility needs to be compiled in static binary. 

