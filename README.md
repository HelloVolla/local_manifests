# Halium/mer-hybris tree local manifest for Volla Phone

This repository contains XML manifest file used to fetch device-specific repositories to build Halium and mer-hybris base for the Volla Phone.

For building Sailfish OS adaptation, use hybris-16.0 branch and follow the official [Hardware Adaptation Development Kit](https://sailfishos.org/develop/hadk/) guide.

# Halium/Ubuntu Touch (UBPorts)
Please check the [Halium documentation](http://docs.halium.org/en/latest/) and [Halium 9 porting notes](https://github.com/ubports/porting-notes/wiki/Halium-9). The basic steps to produce `halium-boot.img` and `system.img` to be used with UBports' Ubuntu Touch rootfs are the following:

```
repo init -u https://github.com/Halium/android -b halium-9.0 --depth=1
mkdir .repo/local_manifests
curl -o .repo/local_manifests/yggdrasil.xml https://raw.githubusercontent.com/HelloVolla/local_manifests/halium-9.0/yggdrasil.xml
repo sync -c
hybris-patches/apply-patches.sh --mb
. build/envsetup.sh
lunch lineage_yggdrasil-userdebug
mka halium-boot systemimage
```
