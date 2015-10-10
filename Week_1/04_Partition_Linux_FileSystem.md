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

> Observe this simple work flow here : https://youtu.be/f_V5LDYaJU8

##LVM : Logical Volume Manager

Once then you have two partition of type `Linux LVM` say,
* /dev/sda5
* /dev/sda6

#####pvcreate
Create a Physical Volume.

Usage :
```sh
pvcreate /dev/sda5 #=> will create a physical Volume.
pvcreate /dev/sda6
```
#####pvs
Show Physical Volumes information

#####pvdisplay
Display attributes of a physical volume.

#####vgcreate
create a Volume Group

```sh
vgcreate vg0 /dev/sda5 /dev/sda6
#vg0 = name of volume group
#following vg0 are members of that volume group
```
#####vgs
Display the volume groups info.

#####lvcreate
Create a logical volume in a given volume group
```sh
lvcreate -L 1G -n lv1 vg0
#-L = length of volume
#-n : name of logical volume
#followed by the group where it should belong
```
After creating the logical volumes,

Now we can see their block files in `/dev` :<br>
* `/dev/vg0/lv1`
* `/dev/vg0/lv2`

We can Now we can make fs :
```sh
mkfs.ext4 /dev/vg0/lv1
mkfs.ext4 /dev/vg0/lv2
```

Mount them as regular partition and done!

> Observe LVM workflow here : https://youtu.be/Nn6_iq5ar4s

####Advantages of LVM :

* LVM gives you more **flexibility** than just using normal hard drive partitions:
* Use any **number of disks as one big disk.**
* Have logical volumes **stretched over several disks.**
* Create small logical volumes and resize them **"dynamically"** as they get filled up.
* Resize logical volumes **regardless of their order** on disk. It does not depend on the position of the LV within VG, there is no need to ensure surrounding available space.
* Resize/create/delete logical and physical volumes **online**. File systems on them still need to be resized, but some (such as ext4) support online resizing.
* Online/live **migration** of LV being used by services to different disks without having to restart services.
* **Snapshots** allow you to backup a frozen copy of the file system, while keeping service downtime to a minimum.
* Support for various device-mapper targets, including transparent filesystem **encryption and caching** of frequently used data.
