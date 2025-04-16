## Enable kernel modules without reflash the system
Follow steps from [here](https://forums.developer.nvidia.com/t/no-ttyusb-ttyacm-shown-after-installed-jetpack6-0/299191/13)
*  ch341 module is needed for RS485  
*  gs_usb module is needed for canable  
### Verify if the module is enabled
The module is enabled if `sudo modprobe` with no error shown.
   e.g. `sudo modprobe gs_usb`

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
      "data-root": "/ssd/docker",
   }
   ```
6. Install [Miniconda](https://www.anaconda.com/docs/getting-started/miniconda/install#aws-graviton2-arm-64) 
* Set install location to "/ssd/miniconda3"
* Set "YES" for updating shell profile to automatically initialize conda    
7. Install curobo in docker
8. Install Firefox, Vscode
