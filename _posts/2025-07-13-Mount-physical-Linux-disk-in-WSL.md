---                                                                                                                                                                                                                                                             
title: Mounting a Physical Linux Disk in WSL
date: 2025-07-13 09:16:00 -0700
categories: [Tutorials, Linux]
tags: [linux, hackery, wsl]
--- 

I have a dual-boot machine, and this is how I access my Linux side while booted into Windows.

## In PowerShell
Find disk path
```
`GET-CimInstance -query "SELECT * from Win32_DiskDrive"
```
Note the PHYSICALDRIVE# value to use in the next command

Attach to default WSL instance (requires administrator rights)
```
wsl --mount \\.\PHYSICALDRIVE6 --bare
```

## In WSL
Create a target directory (once) and mount the filesystem. The `/dev/sdxy` value needed for the mount command can be found by running `sudo lsblk`.
```
sudo mkdir /mnt/linux
sudo mount [-t <filesystem>] [-o <options>] /dev/sdxy /mnt/linux
```

Then bind mount the necessary system mounts.
```
for f in dev sys proc; do sudo mount -o bind /$f /mnt/linux/$f; done
```

Finally, chroot into the system, and mount the rest of the filesystems.
```
sudo chroot /mnt/linux
mount -a
```

## Scripting the actual mount
On my system, which is a LUKS encrypted btrfs partition, I use a script, `mountarch.sh`, which drops me into the chroot, where I still need to run `mount -a` to finish mounting the rest of the Linux filesystems. The mapped device name here (`/dev/mapper/linux-btrfs`) matches the name I use in my `/etc/fstab`.
```
#!/usr/bin/env bash
if [ $1 ]
then
  if [ -b $1 ]
  then
    echo Creating chroot from partition: $1
    cryptsetup open $1 linux-btrfs
    mount -t btrfs -o noatime,compress=zstd,space_cache,subvol=@root /dev/mapper/linux-btrfs /mnt/arch
    for f in dev sys proc; do mount -o bind /$f /mnt/arch/$f; done
    chroot /mnt/arch/ /bin/bash
  else
    echo Partition $1 does not exist.
  fi
else
  echo Please specify target partition.
fi
```

Called with:
`sudo ./mountarch.sh /dev/sdc2` (after checking WSL-assigned device name with `lsblk`)

## Questions? Comments?
Use any of the contact links on this page, especially the Discord server link for assistance.
