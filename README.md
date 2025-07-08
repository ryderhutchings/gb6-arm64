# Geekbench 6

![License](https://img.shields.io/github/license/ryderhutchings/gb6-arm64)
![GitHub Last Commit](https://img.shields.io/github/last-commit/ryderhutchings/gb6-arm64)
![GitHub Issues](https://img.shields.io/github/issues/ryderhutchings/gb6-arm64)
[![YouTube Subscribers](https://img.shields.io/youtube/channel/subscribers/UCfYoumlckdDcox4TtxZiKtA?label=YouTube&style=flat&color=red&logo=youtube)](https://www.youtube.com/@ryderhutchings)


> [!IMPORTANT] 
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
> [!NOTE]
> You might need to re-run the symlink command `sudo ln -sf ~/geekbench6/Geekbench-6.4.0-LinuxARMPreview/geekbench6 /usr/local/bin/geekbench6` in order to ensure the `geekbench6` command works globally.

```bash
mkdir -p ~/geekbench6

wget https://cdn.geekbench.com/Geekbench-6.4.0-LinuxARMPreview.tar.gz -O ~/geekbench6/geekbench.tar.gz

tar -xzf ~/geekbench6/geekbench.tar.gz -C ~/geekbench6

rm ~/geekbench6/geekbench.tar.gz

sudo ln -sf ~/geekbench6/Geekbench-6.4.0-LinuxARMPreview/geekbench6 /usr/local/bin/geekbench6
```

### Using the Tool:

The following usage instructions are from the official Primate Labs documentation:
[Geekbench 6 Command Line Tool](http://support.primatelabs.com/kb/geekbench/geekbench-6-command-line-tool)

If you don't specify any command-line switches, Geekbench 6 runs the CPU benchmark.

Geekbench 6 displays its progress while it's running the workloads, and displays the section scores and overall scores once all the workloads have run. Geekbench 6 will prompt you as to whether you want to upload the results to the Geekbench Browser.

If you don't want to be prompted (for example, you're running Geekbench 6 as part of a script) you can answer this question ahead of time on the command line with one of the following switches:

- `--upload` will automatically upload the result to the Geekbench Browser once the benchmark is complete.
- `--no-upload` will not upload the result to the Geekbench Browser once the benchmark is complete.
You can save Geekbench 6 results with the following command line (note that .gb6 is the recommended file extension for Geekbench 6 results):

`geekbench6 --save result.gb6`

You can also export Geekbench 6 results to different formats. This is a great way to share your results with people who don't have Geekbench 6 installed. Exporting is done with one of the following switches:

- `--export-csv` exports the result as a CSV file.
- `--export-html` exports the result as an HTML file.
- `--export-json` exports the result as a JSON file.
- `--export-text` exports the result as a plain-text file.
You can load and display a saved Geekbench 6 result with the following command line:

`geekbench6 --load result.gb6`

When loading a result, you can manipulate it like any other result. You can upload the saved Geekbench 6 result to the Geekbench Browser by using the following switches:

`geekbench6 --load result.gb6 --upload`

You can also export the saved Geekbench 6 result in a different format. For example, the following command line with export the saved result as an HTML file:

`geekbench6 --load result.gb6 --export-html`

You can view the GPU API available on your system with the following command:

`geekbench6 --gpu-list`

You can then select one GPU compute API to run a benchmark with. For example, we can run an OpenCL benchmark on a system that supports OpenCL with the following command:

`geekbench6 --gpu OpenCL`

If you have multiple GPUs which support the same GPU API, you can differentiate between them with the platform and device ID numbers that appear before the GPU's name after running `geekbench6 --gpu-list`. For example, if the output of `geekbench6 --gpu-list` contains two devices under OpenCL, including `0 1 AMD Radeon VII`, you can run the OpenCL benchmark on the Radeon VII with the following command:

`geekbench6 --gpu OpenCL --gpu-platform-id 0 --gpu-device-id 1`
