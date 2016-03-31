# AMD GPU Set up

1) Download (probably 64-bit) [Version 2.9.1 of AMD OpenCL](http://developer.amd.com/tools-and-sdks/opencl-zone/amd-accelerated-parallel-processing-app-sdk/)
2) Open file manager from Ubuntu Desktop and extract the file. There's a  way
to do it form the command line, but I had trouble with it last time so it's
just easier to do it graphically.
3) Run script navigate to extracted file
```
sudo ./AMD-APP-SDK-v2.9-1.599.381-GA-linux64.sh
```
4) Press enter to navigate through terms of service when it appears.
5) Accept by pressing y
6) Press enter to accept default installation path
7) Create symbolic links
```
sudo ln -s /opt/AMDAPPSDK-2.9-1 /opt/AMDAPP
sudo ln -s /opt/AMDAPP/include/CL /usr/include
sudo ln -s /opt/AMDAPP/lib/x86_64/* /usr/lib/
sudo ldconfig
sudo reboot
```
8) Install fglrx and initialize
```
sudo apt-get install fglrx-updates
sudo aticonfig --adapter=all --initial
sudo aticonfig --list-adapter
```
9) Test and make sure the temperature is returned
```
aticonfig --odgt
```
#### If test failed
1) Edit /etc/default/grub
Add "nogpumanager" in the following line (within the quotation marks)
e.g. if you have this line:
```
GRUB_CMDLINE_LINUX_DEFAULT="quiet splash"
```
it should look like this:
```
GRUB_CMDLINE_LINUX_DEFAULT="quiet splash nogpumanager"
```

2) sudo update-grub
```
sudo update-grub
```

3) Reboot
```
sudo reboot
```

4) Make sure that the following command returns true:
grep nogpumanager /proc/cmdline && echo true || echo false

5) If it returns true, regenerate the xorg.conf
```
sudo aticonfig --adapter=all --initial
```

6) Reboot and see if it all works (attach your /var/log/Xorg.0.log and /etc/X11/xorg.conf)
```
sudo reboot
```
7) repeat test from step 9 in the previous section, if it works move on.
