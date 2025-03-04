### How to build:

1. Establish [Android build environment](https://source.android.com/setup/initializing) and install [repo](https://source.android.com/docs/setup/develop#installing-repo).

2. Initialize repo:

```
repo init -u https://android.googlesource.com/kernel/manifest -b common-android14-6.1-lts
curl -o .repo/local_manifests/manifest_brcm_rpi.xml -L https://raw.githubusercontent.com/clear-code/android_kernel_brcm_rpi_manifest/android-14.0-docker/manifest_brcm_rpi.xml --create-dirs
```

3. Sync source code:

```
repo sync
```

4. Compile:

Raspberry Pi 5:
```
tools/bazel build --config=fast --config=stamp //common:rpi5docker
```

Compiled kernel Image, dtbs, and overlays can be found in `bazel-bin/common/rpi5/arch/arm64/boot` directory.

Replace existing files in `device/brcm/rpi5-kernel` directory of the Android source tree to include them in Android 14 build. You can also replace existing files in the boot partition of Raspberry Pi 5 Android 14 image.
