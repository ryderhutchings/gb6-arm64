# Geekbench 6

![License](https://img.shields.io/github/license/ryderhutchings/gb6-arm64)
![GitHub Last Commit](https://img.shields.io/github/last-commit/ryderhutchings/gb6-arm64)
![GitHub Issues](https://img.shields.io/github/issues/ryderhutchings/gb6-arm64)
[![YouTube Subscribers](https://img.shields.io/youtube/channel/subscribers/UCfYoumlckdDcox4TtxZiKtA?label=YouTube&style=flat&color=red&logo=youtube)](https://www.youtube.com/@ryderhutchings)


> ⚠ **Important:**  
> This project **requires Ubuntu 18.04 LTS (64-bit) or later**

Easy setup script for Geekbench 6 preview on ARM64 (AArch64) Linux devices.

Geekbench doesn't officially support ARM devices; however, on February 16, 2023, Jeff Geerling posted a question to [Geekbench Support](https://support.primatelabs.com/discussions/geekbench/81903-geekbench-6-for-linux-arm64-raspberry-pi-asahi-on-mac-etc?utm_source=chatgpt.com), where staff member John shared a link to download preview builds for ARM.

Later, the official preview page was added:  
https://www.geekbench.com/preview/

This repo was created primarily for personal use, so I could run Geekbench on my ARM devices. However, I thought I’d share this setup for anyone who would like to use it :)

## Disclaimer

This repository provides scripts to automate downloading and running the official Geekbench 6 preview binaries on ARM64 (AArch64) Linux devices.

The official Geekbench package is distributed as a `.tar.gz` archive, which the scripts download and extract automatically.

**Geekbench is proprietary software owned by Primate Labs and is not included in this repository.**  
Users must download the Geekbench binaries only from the official [Geekbench website](https://www.geekbench.com/).

This project is not affiliated with or endorsed by Primate Labs.  
Use these scripts at your own risk.

### Getting Started:

```bash
mkdir -p ~/geekbench6

wget https://cdn.geekbench.com/Geekbench-6.4.0-LinuxARMPreview.tar.gz -O ~/geekbench6/geekbench.tar.gz

tar -xzf ~/geekbench6/geekbench.tar.gz -C ~/geekbench6

rm ~/geekbench6/geekbench.tar.gz

sudo ln -sf ~/geekbench6/geekbench6 /usr/local/bin/geekbench6

