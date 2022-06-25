# myUEFI

# Linux EDK2 Build

## Setup Linux EDK2 build environment

```
sudo apt-get update
sudo apt-get install build-essential
sudo apt-get install nasm
sudo apt-get install iasl

```
## Build and Install NASM 2.15.05
```
wget https://www.nasm.us/pub/nasm/releasebuilds/2.15.05/nasm-2.15.05.tar.xz
tar -xf nasm-2.15.05.tar.xz

cd nasm-2.15.05
./configure --prefix=/usr &&
make

make install

```

## Select the Python3 Version
```
$ export PYTHON_COMMAND=/usr/bin/python3
```

## Download EDK2 SouceCode

```
git clone https://github.com/tianocore/edk2.git
cd edk2
git submodule update --init
cd ..
```

## if need to update Submodules

```
cd edk2
git pull
git submodule update
```

## EDK2 building Setup
```
cd edk2
make -c Basetools
. edksetup.sh Basetools
```

## How to Build OVMF

```
build -p OvmfPkg/OvmfPkgX64.dsc -t GCC5 -a X64
```


## How to Run OVMF in Ubuntu

```
qemu-system-x86_64 -m 4096 -bios bios.bin -nodefaults -display gtk -vga std -drive format=raw,file=fat:rw:/home/chengti/code/ovmf/esp
```
