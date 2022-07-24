# nfsd

## Build Instructions

```bash
git clone https://github.com/dchvs/nfsd.git -b v4.19/standard/qemuarm64
cd nfsd/

S=<linux-yocto @ v4.19 tag>
ARCH=arm64

mkdir build/ && cd build/

make -C ${S} ARCH=${ARCH} defconfig
make -C ${S} ARCH=${ARCH} scripts prepare
make KERNEL_SRC=${S} ARCH=${ARCH} M=${PWD} src=${PWD}/../fs/nfsd
```
