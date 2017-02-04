# linux-vfio

up2date(er) version of https://aur.archlinux.org/packages/linux-vfio

### about
* kernel version `4.9.7`
* (for now) build without `i915 VGA-arbiter`
  * could find matching `.patch` and since I don't use it, I was too lazy to review/fix the latest patch
  * latest (I think) patch is taken from https://lkml.org/lkml/2015/3/4/1184 (see: `0001-i915-Add-module-option-to-support-VGA-arbiter-on-HD-.patch`)
* used `default` ("enter") option for all new flags
* most important (for my use case was `ACS overrides`)
  ```
   f4bio@d3sktop ~  $ uname -a
  Linux d3sktop 4.9.7-1-vfio #2 SMP PREEMPT Sat Feb 4 05:00:28 CET 2017 x86_64 GNU/Linux
   f4bio@d3sktop ~  $ iommu-groups
  IOMMU Group 0 00:00.0 Host bridge [0600]: Intel Corporation 4th Gen Core Processor DRAM Controller [8086:0c00] (rev 06)
  IOMMU Group 10 00:1c.6 PCI bridge [0604]: Intel Corporation 8 Series/C220 Series Chipset Family PCI Express Root Port #7 [8086:8c1c] (rev d5)
  IOMMU Group 11 00:1d.0 USB controller [0c03]: Intel Corporation 8 Series/C220 Series Chipset Family USB EHCI #1 [8086:8c26] (rev 05)
  IOMMU Group 12 00:1f.0 ISA bridge [0601]: Intel Corporation Z87 Express LPC Controller [8086:8c44] (rev 05)
  IOMMU Group 12 00:1f.2 SATA controller [0106]: Intel Corporation 8 Series/C220 Series Chipset Family 6-port SATA Controller 1 [AHCI mode] [8086:8c02] (rev 05)
  IOMMU Group 12 00:1f.3 SMBus [0c05]: Intel Corporation 8 Series/C220 Series Chipset Family SMBus Controller [8086:8c22] (rev 05)
  IOMMU Group 13 01:00.0 VGA compatible controller [0300]: NVIDIA Corporation GK106 [GeForce GTX 660] [10de:11c0] (rev a1)
  IOMMU Group 13 01:00.1 Audio device [0403]: NVIDIA Corporation GK106 HDMI Audio Controller [10de:0e0b] (rev a1)
  IOMMU Group 14 02:00.0 VGA compatible controller [0300]: Advanced Micro Devices, Inc. [AMD/ATI] RV710 [Radeon HD 4350/4550] [1002:954f]
  IOMMU Group 14 02:00.1 Audio device [0403]: Advanced Micro Devices, Inc. [AMD/ATI] RV710/730 HDMI Audio [Radeon HD 4000 series] [1002:aa38]
  IOMMU Group 15 04:00.0 SATA controller [0106]: ASMedia Technology Inc. ASM1062 Serial ATA Controller [1b21:0612] (rev 01)
  IOMMU Group 16 05:00.0 Network controller [0280]: Intel Corporation Wireless 7260 [8086:08b1] (rev bb)
  IOMMU Group 1 00:01.0 PCI bridge [0604]: Intel Corporation Xeon E3-1200 v3/4th Gen Core Processor PCI Express x16 Controller [8086:0c01] (rev 06)
  IOMMU Group 2 00:01.1 PCI bridge [0604]: Intel Corporation Xeon E3-1200 v3/4th Gen Core Processor PCI Express x8 Controller [8086:0c05] (rev 06)
  IOMMU Group 3 00:14.0 USB controller [0c03]: Intel Corporation 8 Series/C220 Series Chipset Family USB xHCI [8086:8c31] (rev 05)
  IOMMU Group 4 00:16.0 Communication controller [0780]: Intel Corporation 8 Series/C220 Series Chipset Family MEI Controller #1 [8086:8c3a] (rev 04)
  IOMMU Group 5 00:19.0 Ethernet controller [0200]: Intel Corporation Ethernet Connection I217-V [8086:153b] (rev 05)
  IOMMU Group 6 00:1a.0 USB controller [0c03]: Intel Corporation 8 Series/C220 Series Chipset Family USB EHCI #2 [8086:8c2d] (rev 05)
  IOMMU Group 7 00:1b.0 Audio device [0403]: Intel Corporation 8 Series/C220 Series Chipset High Definition Audio Controller [8086:8c20] (rev 05)
  IOMMU Group 8 00:1c.0 PCI bridge [0604]: Intel Corporation 8 Series/C220 Series Chipset Family PCI Express Root Port #1 [8086:8c10] (rev d5)
  IOMMU Group 9 00:1c.3 PCI bridge [0604]: Intel Corporation 8 Series/C220 Series Chipset Family PCI Express Root Port #4 [8086:8c16] (rev d5)
  ```
* dropped `i686` like arch will do soon enough
