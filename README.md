# nfsd

## Build Instructions

```bash
git clone https://github.com/dchvs/nfsd.git -b v4.19/standard/qemuarm64
cd nfsd/

S=${PWD}/
K=<linux-yocto @ v4.19 tag>
KTF_HEADERS=<KTF Kernel headers>
B=${S}/build
O=${B}/output

ARCH=arm64

mkdir -p ${B} && cd ${B}

make -C ${K} ARCH=${ARCH} defconfig
make -C ${K} ARCH=${ARCH} scripts prepare
rsync ${S}/fs/nfsd/Makefile ${B}
make KERNEL_SRC=${K} ARCH=${ARCH} KTF_HEADERS=${KTF_HEADERS} CROSS_COMPILE=${CROSS_COMPILE} S=${S} src=${S}/fs/nfsd/
```
