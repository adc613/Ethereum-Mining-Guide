# Step 1 Create a Bootable Flash Drive 
1. [Download Ubuntu 14.04 (64 bit)](http://www.ubuntu.com/download/desktop/thank-you?country=US&version=14.04.4&architecture=amd64)
2. convert iso file to an image file
```
hdutil convert -format UDRW -o ~/path/to/target.img ~/path/to/ubuntu.iso
```
On my machine:
```
hdiutil convert -format UDRW -o ~/Desktop/ubuntu.img ~/Downloads/ubuntu-14.04.4-desktop-amd64.iso
```
3. Run
```
diskutil list
```
You will see an output like this
```
/dev/disk0 (internal, physical):   
#:                       TYPE NAME                    SIZE       IDENTIFIER   
0:      GUID_partition_scheme                        *251.0 GB   disk0   
1:                        EFI EFI                     209.7 MB   disk0s1   
2:                  Apple_HFS Macintosh HD            200.0 GB   disk0s2   
3:                 Apple_Boot Recovery HD             650.0 MB   disk0s3   
4:       Microsoft Basic Data BOOTCAMP                50.1 GB    disk0s4
/dev/disk1 (external, physical):   
#:                       TYPE NAME                    SIZE       IDENTIFIER   
0:     Apple_partition_scheme                        *16.0 GB    disk1   
1:        Apple_partition_map                         4.1 KB     disk1s1   
2:                  Apple_HFS                         2.3 MB     disk1s2 
```
Look for your USB drive on the list, in my case is "/dev/disk1" Yours will be
some variation always ending in some number (N). For the next two steps I will
use /dev/diskN/ as a placeholder. (consequently /dev/rdiskN/ would correspond
to /dev/rdisk1/)
4. Run
```
diskutil unmountDisk /dev/diskN
```
5. run
```
sudo dd if=/path/to/download.img of=/dev/rdiskN bs=1m
```
in my case

```
sudo dd if=~/Desktop/ubuntu.img.dmg of=/dev/rdisk1 bs=1m
```
6. Let it the process run it make take a few minutes (be patient), then eject
   from the command line by running
```
diskutil eject /dev/disk1
```
7. Insert into your mining rig and boot to the BIOS
