##Switch to root user:
    1- sudo -i
    
##  Step 1: Create Virtual Disk :
    dd if=/dev/zero of=/tmp/disk1.img bs=1M count=1024
    losetup -fP /tmp/disk1.img
    losetup -a 
    ##output :
         /dev/loop0: [2065]: (/tmp/disk1.img)

##  Task 1: Check Current Storage: 
    1- lsblk - check the current block storage.
    2- pvs - display info about physical volume.
    3- vgs - shows the details of volume
    4- lvs - list the all logical volume
    5- df -h - show the disk space usages in human readable format
   ##ss add
   
## Task 2: Create Physical Volume:
    1- pvcreate /dev/loop - initializes the device as a physical volume
    2- pvs  - display info about physical volume
   ##ss add 
   
## Task 3: Create Volume Group:
    1- vgcreate devops-vg dev/sdb - Creates a Volume Group named devops-vg using the Physical Volume /dev/loop0
    2- vgs - show the details of volume.
   ##ss add

## Task 4: Create Logical Volume:
    1- lvcreate -L 500M -n app-data devops-vg - Creates a 500MB Logical Volume named app-data inside the devops-vg
    2- lvs - list the all logical volume
   ##ss add 

## Task 5: Format and Mount:
    1- mkfs.ext4 /dev/devops-vg/app-data - formats the logical volume with ext4 filesystem
    2- mkdir -p /mnt/app-data - creates the mount directory
    3- mount /dev/devops-vg/app-data /mnt/app-data - mounts the logical volume to the directory
    4- df -h /mnt/app-data - show the disk usage of the mounted volume in human readble format
   ##ss add 

## Task 6: Extend the Volume:
    1- lvextend -L +200 /dev/devops-vg/app-data - increase the logical volume of size by 200MB 
    2- resizes2fs /dev/devops-vg/app-data - expands the file system to use the new space
    3- df -h /mnt/app-data - verify the update disk size in human readable format
   ##ss add

## What I Learned:
    1- LVM allows flexible storage management without downtime
    2- We can extend storage without deleting or recreating partitions
    3- Logical Volumes can be resized dynamically based on need
   
    
    
    

    
         

          
    
    
    
    
