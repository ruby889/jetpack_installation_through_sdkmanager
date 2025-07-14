## Enable kernel modules without reflash the system
1. Download `Driver Package (BSP) Sources` from [here](https://developer.nvidia.com/embedded/jetson-linux-r3643).  
2. For rt_kernel, enable the real-time configuration as shown [here](https://docs.nvidia.com/jetson/archives/r36.4.3/DeveloperGuide/SD/Kernel/KernelCustomization.html#building-the-jetson-linux-kernel).  
3. Follow steps from [here](https://forums.developer.nvidia.com/t/no-ttyusb-ttyacm-shown-after-installed-jetpack6-0/299191/13).  
*  ch341 module is needed for RS485  (Linux_for_Tegra/source/kernel/kernel-jammy-src/drivers/usb/serial/ch341.ko)
*  gs_usb module is needed for canable (Linux_for_Tegra/source/kernel/kernel-jammy-src/drivers/net/can/usb/gs_usb.ko)
### Verify if the module is enabled
The module is enabled if `sudo modprobe` with no error shown.
   e.g. `sudo modprobe gs_usb`
### Alternative tutorial
* JetsonHacks - [Build Jetson Orin Kernel and Modules](https://jetsonhacks.com/2025/03/13/build-jetson-orin-kernel-and-modules/)

## Installation list for new Jetson  
1. Install Jetpack6.2  
2. Configure SSD  
3. Install real-time kernel  
4. Allow docker access for non-root user from [here](https://docs.docker.com/engine/install/linux-postinstall/#manage-docker-as-a-non-root-user)
5. Edit /etc/docker/daemon.json. Change the `data-root` to sdd and add `default-runtime` for using Curobo. 
   ```
   {
      "runtimes": {
         "nvidia": {
               "path": "/usr/bin/nvidia-container-runtime",
               "runtimeArgs": []
         }
      },
      "default-runtime": "nvidia",
      "data-root": "/ssd/docker"
   }
   ```
* Restart docker for the configuration file to take effect.
   ```
   sudo systemctl start docker
   sudo systemctl daemon-reload
   sudo systemctl restart docker
   ```
6. Install [Miniconda](https://www.anaconda.com/docs/getting-started/miniconda/install#aws-graviton2-arm-64) 
* Set install location to "/ssd/miniconda3"
* Set "YES" for updating shell profile to automatically initialize conda    
7. Install curobo in docker
8. Install Firefox, Vscode
