### Steps to build your own kernel!!@! trust me
- Download a generic kernel (anyone on your distro repo)
- Load your system (most difficult step)
- Download the version of the kernel you want ([kernel.org](https://kernel.org)) and execute `make localmodconfig` (this will make that your loaded modules at the moment of execution will be saved into a .config file, in that way you disable any other module that your system are not goona use)
- Copy it to srcpkgs/pkg or compile your kernel there.

### Why I WOULD compile my own kernel?
generic kernels came with 5k modules at least, why? because they're generic, that's obvious. they want to provide support for systems from even 1998. when you compile only the modules you need, that numbers decrease to just ~220 modules. also, you can add patches like the zen-kernel one, select the compression and de-compression algorithm (zstd), memory, crypto, debug options, etc. you have the control over your system. Also, if you decrease the modules enabled, you are decreasing the compile time. In my case, i enabled a option that is not available on the generic one, that is related to XDNA.

<img width="1035" height="671" alt="image" src="https://github.com/user-attachments/assets/51b47a5f-04eb-45e0-abdf-dfbbd2324e54" />

### Bro what do y, m and n mean into .config?
the linux kernel is a monolithic one. `y` means that module will be compile inside of the linux kernel image (vmlinuz), `m` means that you include that module, but not inside of the kernel, but as a module, that would be stored inside of `initramfs`. `with `n` or commenting it you are excluding modules. 

### What's the deal with xbps-src?
xbps-src workflow is: binary-bootstrap -> build package into the virtual host -> install it to your system. xbps packages are attached with the package name, version and revision. every package have a lot of versions, but also can have a bunch of revisions. by default it's `package-version_1`, like `linux7.0-7.0.3_1`.

### Linux 7.0 zen
| Kernel | vmlinuz  | initramfs.img |
| - | ------------- | ------------- |
| 🦃 Linux Stable | 14MB  | 146MB  |
| 🦃 Linux Zen | 11MB  | 43MB  |

<br />
<img width="809" height="337" alt="image" src="https://github.com/user-attachments/assets/d5494243-915a-4933-bed5-60da7f269b94" />

### Linux 6.17 zen

`linux6.17-zen` ([click here](https://github.com/hyduez/void-packages/tree/master/srcpkgs/linux6.17-zen)) is optimized for Ryzen 5 8600G. A Zen 4 monolithic CPU (Phoenix architecture), with 2 NPUs from Ryzen AI (XDNA drivers). Also dual-channel DDR5 and NVME configuration. All debugging options disabled, Intel and NUMA disabled. Power saving is not useful at all because I use a desktop computer, so the power supply is managed by AMD drivers and PSU itself. Everything works, at least in my environment, where I use virtual machines, Waydroid, and KVM.

`mirror.linux.ec/voidlinux` is the mirror I set up in /etc/xbps.d/ because I live in Ecuador, that's all. Initramfs is created with mkinitpcio instead of dracut. (Reduction from 200 MB to 32 MB). The kernel is compiled using ZSTD instead of GZIP, which increases decompression speed.


| Kernel | vmlinuz  | initramfs.img |
| - | ------------- | ------------- |
| 🦃 Linux Stable | 13MB  | 146MB  |
| 🦃 Linux Mainline | 13MB  | 200MB  |
| 🦃 Linux Zen | 9MB  | 32MB  |

<br />
<img width="1041" height="544" alt="image" src="https://github.com/user-attachments/assets/227f2d4b-c82d-43ab-959f-1b50c0eac744" />
