# ScaleLFS: A Log-Structured File System with Scalable Garbage Collection for Commodity SSDs

## Build/install kernel/module
* Do the same step to the existing kernel build and installation

```bash
cd ScaleLFS
make

* RLW module can be found at ScaleLFS/scalelfs.ko

## Build mkfs
* Prepare mkfs module in f2fs-tools with "git submodule"

```bash
cd ScaleLFS/f2fs-tools
./autogen.sh
./configure
make

## Usage (example for mounting /dev/nvme0n1 to directory /mnt with 32 DGCs)
```bash
sudo insmod ScaleLFS/scalelfs.ko num_gc_thread=32
sudo ScaleLFS/f2fs-tools/mkfs/mkfs.f2fs /dev/nvme0n1
mount -t f3fs /dev/nvme0n1 /mnt -o lfs
