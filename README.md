# The AMDGPU-PRO AMF Video Encoder
<https://github.com/GPUOpen-LibrariesAndSDKs/AMF>

This is a PKGBUILD for setting up AMF on Arch Linux systems with AMD GPUs.

**This encoder utilizes aspects of the AMDVLK-PRO driver for Vulkan compute, so it requires ffmpeg or obs to be run using AMDVLK-pro instead of AMDVLK-free or RADV.**

## Dependencies
- TK-Glitch's [amdgpu-pro-vulkan-only](https://github.com/Frogging-Family/amdgpu-pro-vulkan-only) PKGBUILD
- [ffmpeg-amd-full-git](https://aur.archlinux.org/packages/ffmpeg-amd-full-git)

## Build
```sh
git clone https://github.com/durcor/amdgpu-pro-amf-only.git
cd amdgpu-pro-amf-only
makepkg -si
```

## Usage
```sh
VK_ICD_FILENAMES=/opt/amdgpu-pro/etc/vulkan/icd.d/amd_icd64.json:/opt/amdgpu-pro/etc/vulkan/icd.d/amd_icd32.json
ffmpeg -f x11grab -s 1920x1080 -r 60 -i $DISPLAY -c:v h264_amf test.mp4
```

or if you are using obs:

```sh
VK_ICD_FILENAMES=/opt/amdgpu-pro/etc/vulkan/icd.d/amd_icd64.json:/opt/amdgpu-pro/etc/vulkan/icd.d/amd_icd32.json 
obs
```

## Quirks
- hevc_amf does not appear to be supported at the moment, at least on Navi, so h264_amf appears to be the only working implementation currently
