tags: #linux 
# Listing the GPU Devices
```bash
sudo apt install lshw
sudo lshw -C display
```

# Checking which GPU is Being Used

The `glxgears` package can be used to check which GPU is being used to render in OpenGL:

```bash
sudo apt install mesa-utils
glxgears -info
```

Look at the very top of the output and look for the `GL_RENDERER`, `GL_VERSION`
and `GL_VENDOR` variables.
# See what Nvidia stuff is installed
The command below will list out everything related to NVidia that has been installed.

```bash
dpkg -l | grep nvidia
```

# Installing Nvidia Driver

Instructions [here](https://ubuntu.com/server/docs/nvidia-drivers-installation)
## 1 - Remove the current Nvidia drivers:

```bash
sudo apt-get purge 'nvidia-*'
sudo apt-get purge '^nvidia-.*'
sudo apt-get autoremove
```
## 2 - Install Driver
See what drivers are available, and then install the one I want:

```bash
sudo ubuntu-drivers list
sudo ubuntu-drivers install nvidia:470
```

# Black listing NVidia Drivers and Devices

You can blacklist modules by editing the `/etc/modprobe.c/blacklist.conf` file, and adding:

```bash
blacklist nouveau
blacklist nvidia
blacklist nvidia-drm
blacklist nvidia-modeset
```

When you edit this file you need to run:

```bash
sudo update-initramfs -u
reboot
```
