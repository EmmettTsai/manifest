The Android Open Source Project Oreo 8.0.0_r1
===========

Initializing repository
````bash
repo init -u git://github.com/EmmettTsai/manifest.git -b flo-oreo-test
````

Initialized to be downloaded with the kernel source
````bash
repo init -u git://github.com/EmmettTsai/manifest.git -b flo-oreo-test -g default,kernel-source
````

Sync code
````bash
repo sync
````

Setup and Launch
````bash
source build/envsetup.sh
lunch aosp_flo-userdebug
````

Build kernel
````bash
cd $KERNEL_SRC_DIR
export ARCH=arm
export SUBARCH=arm
export CROSS_COMPILE=arm-linux-androideabi-
make flo_defconfig
make -j8
export TARGET_PREBUILT_KERNEL=$KERNEL_SRC_DIR/arch/arm/boot/zImage
````

Build ota
````bash
cd $ANDROID_BUILD_TOP
make -j8 otapackage
````

