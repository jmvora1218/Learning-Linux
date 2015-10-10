# Partitioning Linux FileSystem


##fdisk Command
#####fdisk
/dev/sda -> select the secondary storage drive.

```sh
m = help
n = new Partition
p = display partition table
w = write quit
d = delete partition
```
Note : Th ere can be only 4 primary partition but any number of logical partition

#####partprobe
 inform the OS of partition table changes then use.

```sh
mkswap #partition type should be LINUX SWAP to use this
mkfs.ext3 #makes ext3 filesystem
mkfs.ext4 #makes ext4 file system
mkfs -t ext4 /dev/sda3  #-t as a type flag
```

  Now once after creating a partition we can mount by : mount command <br>
  But the changes are pertaining to only the reboot.

    - To make the chages persist accross reboot we have to make a entry in /etc/fstab

    - The fields in fstab are as :
```sh  
    <filesystem>    <mount-point> <type> <option> <dump> <pass>
  ex/dev/sda3     /newpartition ext4  defaults  0       0
  #dump = no back => val=1 take back up everyday , 2 = backup every alternate day
  # pass = 1 check fs in begining (first fs to be checked), 2 check after 1
```  
  after making changes,
```sh  
mount -a #mount all entries in etc/fstab file.  
mount    #cmd to display what is mounted.
```

#####Extended Partition
Logical Partition needs to be created on the Extended partition to make it usable.

  - Logical Volume Arrangement in Linux : LVM
  - All the partitions in the LVM should be of type "Linux LVM"
  - The hex code for Linux LVM in fdisk is 8e
  - fdisk t = change type

After making partitions on the same (Logical Partitions) you can follow the same steps to continue with making FS and using it.

##LVM : Logical Volume Manager

  Once then you have LVM say,<br>
  /dev/sda5 <br>
  /dev/sda6 <br>

* use 'pvcreate /dev/sda5' => will create a **physical Volume**.
* use 'pvs' -> reports information about physical Volumes.
* use 'pvdisplay' -> display attributes of a physical volume.

*  Now use **vgcreate** command to create a volume group.
  ```
    vgcreate vg0 /dev/sda5 /dev/sda6
```
   - Now 'vgs' to display the volume groups info.

* now create a **logical volume**
    ```
    lvcreate -L 1G -n lv1 vg0
```
    Now we can see their paths as :<br>
    /dev/vg0/lv1 <br>
    /dev/vg0/lv2

    Now we can make fs : <br>
    mkfs.ext4 /dev/vg0/lv1 <br>
    mkfs.ext4 /dev/vg0/lv2

  Mount them as regular partition and done!
