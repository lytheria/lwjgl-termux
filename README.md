[![License: BSD 3-Clause License](https://img.shields.io/badge/License-BSD_3--Clause-blue.svg)](https://opensource.org/licenses/BSD-3-Clause)
[![Termux](https://img.shields.io/badge/Environment-Termux-alpha.svg)](https://termux.dev)
[![Platform: Android](https://img.shields.io/badge/Platform-Android-green.svg)](https://www.android.com)
[![GitHub Profile](https://img.shields.io/badge/GitHub-Profile-181717?style=flat&logo=github)](https://github.com/lytheria)

# <img src="https://github.com/user-attachments/assets/c7c318ab-4b61-4cee-9a14-13f34edafd6e" width="4%"> LWJGL Termux</img>

This repository provides a guide and necessary binaries/scripts to run **LWJGL (Lightweight Java Game Library)** seamlessly inside the **Termux** environment on Android. Perfect for running Minecraft Java Edition, game development, or any Java-based OpenGL applications that needed LWJGL.

---

## 📌 Specifications
* **Hardware Acceleration:** Compatible with Mesa `(virgl/zink/freedreno)` or other drivers for hardware-accelerated rendering. 🖥️
* **Architecture:** Supported 64-bit (ARM64) device only. 📱

---

## 📸 Screenshot

<p align="center">
  <img width="70%" height="70%" alt="1000757790" src="https://github.com/user-attachments/assets/1fafa42c-a078-402e-82c6-659c4a3f3352" />
</p>

---

Minecraft (OptiFine) 1.20.1 using Chocapic13 V6 Low shaders on Termux (without Proot/Chroot) with the Mesa3D Zink OpenGL 4.6 (Core Profile) driver on a Mali-G52 GPU. The Mesa3D OpenGL Core Profile lets you play Minecraft 1.17.x and later using shaderpacks without graphical bugs, while delivering better performance on modern mobile devices and giving you full control to tweak and customize your Minecraft experience in Termux. ✨

---

## 📥 Installation

For example, run the following commands to quickly install LWJGL and other programs. 🤗

&ensl;Update & Upgrade Termux essentials:
```
pkg update && pkg upgrade -y
```

&ensp;wget:
```
pkg install wget -y
```
&ensp;LWJGL:
```
wget https://github.com/lytheria/lwjgl-termux/releases/download/3.3.6/lwjgl-termux-3.3.6_aarch64.deb && dpkg -i lwjgl-termux-3.3.6_aarch64.deb
```
&ensp;Termux User Repository (TUR):
```
pkg install tur-repo -y
```
&ensp;Java OpenJDK-17:
```
pkg install openjdk-17 -y
```
&ensp;X11 and dependencies:
```
pkg install x11-repo && pkg update && pkg install libandroid-shmem libdrm libexpat libexpat-static zstd zlib libxcb libx11 libc++ && pkg install termux-x11 xorgproto libxxf86vm libglvnd-dev mesa-dev libwayland vulkan-loader libxxf86dga libxrandr libx11-static libxext
```
&ensp;Install OpenGL Drivers:<br>
<br>
&ensp;&ensp;• freedreno for Adreno GPU (required GPU Adreno 6xx):<br>
```
pkg install mesa-vulkan-icd-freedreno -y
```
&ensp;&ensp;• zink For all GPUs that support Vulkan (required Vulkan 1.2):<br>
```
pkg install mesa
```
&ensp;&ensp;• or zink my build version (required Vulkan 1.1):
```
wget https://github.com/lytheria/mesa-zink-opengl/releases/download/23.x.x/mesa-zink-opengl-23.0.0_aarch64.deb && find ~ -name mesa-zink-opengl-23.0.0_aarch64.deb -exec dpkg -i {} +
```
&ensp;&ensp;• VirGL for all GPUs that support OpenGL ES only (required OpenGL ES 3.0):
```
pkg install virglrenderer-android
```
&ensp;Setup LWJGL and Minecraft libraries:
```
export CP="$PREFIX/lwjgl3/*:/path/to/your/minecraft/modules/libraries:$CP"
```
&ensp;Setup Display and X11 server:
```
export DISPLAY=:0 && termux-x11 :0 2> /dev/null &
```

Then run Minecraft program `java -cp $CP net.minecraft.client.Main`. For example, see [`OptiFine.sh`](https://drive.google.com/file/d/1yJY3bzfAYL5Lpenvum3lMsa20p2y5Tbx/view?usp=sharing) as your reference. 📖


## ✏️ Guide to use OpenGL drivers
For example,`export MESA_LOADER_DRIVER_OVERRIDE=zink && export GALLIUM_DRIVER=zink` run these commands to enable Zink. or `export MESA_LOADER_DRIVER_OVERRIDE=freedreno && export GALLIUM_DRIVER=freedreno` run these commands to enable freedreno. or `export GALLIUM_DRIVER=virpipe && export VTEST_SOCK=$PREFIX/tmp/.virgl_test && virgl_test_server &` run these commands to enable VirGL. And `export MESA_GL_VERSION_OVERRIDE=4.6  && export MESA_GLSL_VERSION_OVERRIDE=460` run these commands to override the OpenGL version (but max version for VirGL is GL 4.5 and GLSL 450). To enable OpenGL Core Profile, run the following command `MESA_GL_VERSION_OVERRIDE=4.6FC`. If you use my zink build version, see [Key Features](https://github.com/lytheria/mesa-termux#key-features) to get more information.

---

## 🧑‍💻 Author

Managed and maintained by [@Lytheria](https://github.com/lytheria).
If you have questions, feature requests, or want to collaborate on optimizing Mesa for Termux, feel free to open an issue or connect via my [GitHub Profile](https://github.com/lytheria).

---
