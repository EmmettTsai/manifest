The Android Open Source Project Pie 9.0.0_r21
===========

Initializing repository
````bash
repo init -u https://android.googlesource.com/platform/manifest -b android-9.0.0_r21
````

Initialized to be downloaded with the kernel source
````bash
repo init -u https://android.googlesource.com/platform/manifest -b android-9.0.0_r21 -g default,kernel-source
````

Setup local manifests
````bash
git clone https://github.com/EmmettTsai/manifest.git
git checkout origin/flo-aosp-pie

copy local_manifests to ~/path_to_aosp_root/.repo/

ex:
~/Project/aosp/android-9.0.0_r21/.repo/local_manifests/emmett_tsai.xml
````

Sync code
````bash
repo sync
````

Setup and Launch
````bash
source build/envsetup.sh
lunch full_flo-userdebug
````

Build kernel (option)
````bash
cd $KERNEL_SRC_DIR
PATH=$ANDROID_BUILD_TOP/prebuilts/gcc/linux-x86/arm/arm-eabi-4.8/bin:$PATH
export ARCH=arm
export SUBARCH=arm
export CROSS_COMPILE=arm-eabi-
make followmsi-aosp_defconfig
make -j8
export TARGET_PREBUILT_KERNEL=$KERNEL_SRC_DIR/arch/arm/boot/zImage
````

Build ota
````bash
cd $ANDROID_BUILD_TOP
make -j8 otapackage
````

Thanks to followmsi, LineageOS, and google
https://github.com/followmsi
https://github.com/LineageOS

device and vendor project fork from followmsi.

kernel fork from followmsi pie and merge LineageOS 16.0.

hardware project is base on aosp android-9.0.0_r21 and then pick some patch from followmsi.

