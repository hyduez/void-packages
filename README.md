`linux6.17-zen` ([click here](https://github.com/hyduez/void-packages/tree/master/srcpkgs/linux6.17-zen)) is optimized for Ryzen 5 8600G. A Zen 4 monolithic CPU (Phoenix architecture), with 2 NPUs from Ryzen AI (XDNA drivers). Also dual-channel DDR5 and NVME configuration. All debugging options disabled, Intel and NUMA disabled. Power saving is not useful at all because I use a desktop computer, so the power supply is managed by AMD drivers and PSU itself. Everything works, at least in my environment, where I use virtual machines, Waydroid, and KVM.

`mirror.linux.ec/voidlinux` is the mirror I set up in /etc/xbps.d/ because I live in Ecuador, that's all. Initramfs is created with mkinitpcio instead of dracut. (Reduction from 200 MB to 32 MB). The kernel is compiled using ZSTD instead of GZIP, which increases decompression speed.


| Kernel | vmlinuz  | initramfs.img |
| - | ------------- | ------------- |
| 🦃 Linux Stable | 13MB  | 146MB  |
| 🦃 Linux Mainline | 13MB  | 200MB  |
| 🦃 Linux Zen | 9MB  | 32MB  |

<br />
<img width="1041" height="544" alt="image" src="https://github.com/user-attachments/assets/227f2d4b-c82d-43ab-959f-1b50c0eac744" />
