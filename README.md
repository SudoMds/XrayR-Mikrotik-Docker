## XrayR-Mikrotik-Docker
An easy-to-use, precompiled XrayR Docker image for MikroTik devices.

# Requirements
MikroTik CHR or compatible device with:

x86_64 or armv7 (x86) architecture

Container support enabled

Basic knowledge of MikroTik RouterOS

# Docker container setup on your MikroTik device

# Docker Images
Choose the appropriate image for your architecture:

ARMv7: dashti75/xrayr-mikrotik-armv7

x86_64: dashti75/xrayr-mikrotik-x86_64

# Installation Steps
Prepare the configuration directory:

# Code
/disk1/config/
Place your config.yml file in this directory.

Create a mount point in RouterOS:

# Code
/container/mounts add name=xrayr_config src=/disk1/config dst=/mnt/config
Pull and run the container:

# Code
/container add remote-image=dashti75/xrayr-mikrotik-[ARCH] interface=veth1 root-dir=/xrayr mount=xrayr_config
Replace [ARCH] with either armv7 or x86_64 based on your device.

Start the container:

# Code
/container start [container-name]
The service will automatically load your configuration from /mnt/config/config.yml.

# Notes
Ensure your MikroTik device has sufficient resources to run containers

The container will look for the configuration file at /mnt/config/config.yml by default

Make sure your config.yml is properly formatted before starting the container

Support
For issues or questions, please open an issue in the GitHub repository.
