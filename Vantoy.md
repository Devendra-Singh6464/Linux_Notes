## Multi iso bootable Pandrive----
 
1. Install vantoy tar file 
```
https://ventoy.net/en/download.html
```
2. After install tar file untar the file. 
```
tar -xf filename.tar
```
3. Go this ​directory---
```
ventoy-1.0.99
```
4. Run script
```
./Ventoy2Disk.sh
```
5. Then cleck USB mount location
```
lsblk
```
7. Your USB mount location here-
```
syntax-- /media/<user_name>/
/media/devendra.singh/
```
6. Then run this command -
Sysntax-
/Ventoy2Disk.sh -i /dev/file_name
```
/Ventoy2Disk.sh -i /dev/sdd
```
5. After this script run you got error-
```
Error: Failed to access /dev/sdc, maybe root privilege is needed!
```
8. After Go to root and run again this command-----  
```
/Ventoy2Disk.sh -i /dev/sdd
```
9. If you got this error `/dev/sdd is already mounted, please umount it first!`
----please unmount /dev/sdd
```
umount /dev/sdd
```
