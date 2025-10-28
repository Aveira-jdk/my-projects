# Linux From Scratch — Custom UEFI Build
**Date:** September 5, 2025  
**Type:** Solo project

## Goal
Build a fully working Linux system 100% from source (toolchain, core utilities, kernel, bootloader), not using a normal distro installer — and make it boot under **UEFI** from an **external NVMe SSD**.

This was done following Linux From Scratch (LFS) methodology with some BLFS additions.

---

## What Was Built
- A working LFS 12.x system that boots via **UEFI + GRUB**.
- Custom-compiled **Linux kernel**, configured manually, rebuilt multiple times.
- Full base userland built from binutils, glibc, gcc, coreutils, etc.
- Extra tooling from BLFS:
  - `zsh` as an alternative shell
  - `nano` as an extra text editor
- System lives on an external NVMe SSD and boots independently.

---

## Major Technical Challenges Solved
### 1. UEFI vs Legacy Boot
- Started with UEFI (GPT), then tested BIOS/MBR.
- Ran into mixed-mode problems (GPT + legacy boot, leftover UEFI artifacts).
- Final result: clean UEFI boot with GRUB on the external SSD.

### 2. Kernel Configuration
- Early attempts without `menuconfig` caused missing drivers.
- Rebuilt the kernel 4–5 times until it included:
  - **USB3 support**
  - **NVMe storage support**
- Once those were enabled, the external NVMe could finally be used as the root filesystem.

### 3. Device Naming / Stability
- `/dev/sda` vs `/dev/sdb` kept changing depending on boot order.
- Fixed by switching GRUB and `/etc/fstab` to use **UUID/PARTUUID** instead of hard-coded device names.

---

## Key Technologies
- Linux kernel
- GCC toolchain (binutils, glibc, gcc)
- Coreutils / base system libraries
- GRUB (UEFI bootloader)
- Bash, zsh, nano
- Custom `/etc/fstab` and GRUB configs using UUIDs for portable booting

---

## Result
On September 9, 2025:
- The system successfully booted via UEFI from the external NVMe SSD.
- GRUB menu worked.
- Kernel loaded with correct drivers (USB3 + NVMe).
- Shell environment available with both bash and zsh.

---

## Why This Matters
This project demonstrates:
- Deep understanding of Linux internals (not just using a distro).
- Ability to debug kernel boot failures.
- Comfort with UEFI, GRUB, and low-level system layout.
- Ability to produce a self-contained, portable Linux environment starting from source.
