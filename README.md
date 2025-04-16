## Enable kernel modules without reflash the system
Follow steps from [here](https://forums.developer.nvidia.com/t/no-ttyusb-ttyacm-shown-after-installed-jetpack6-0/299191/13)
*  ch341 module is needed for RS485  
*  gs_usb module is needed for canable  
### Verify if the module is enabled
The module is enabled if `sudo modprobe` with no error shown.
   e.g. `sudo modprobe gs_usb`
