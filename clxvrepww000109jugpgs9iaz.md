---
title: "Create bootable USB with Linux image in Linux"
datePublished: Wed Jun 26 2024 11:35:50 GMT+0000 (Coordinated Universal Time)
cuid: clxvrepww000109jugpgs9iaz
slug: create-bootable-usb-with-linux-image-in-linux
tags: linux, linux-for-beginners, linux-basics, bootable

---

To make USB bootable with a linux os in linux you'll need a USB that has enough storage. Usually 8gb USB is enough to install any operating system. As we have the USB, insert the USB to the machine. Let's see how we can make it Bootable. In this turorial, I'll make a USB bootable with Pop OS and I'm currently using Manjaro XFCE distro. It should work same for all linux distros. Let's get started.

As we have inserted the USB to the machine, we can check its name by this command.

```bash
sudo fdisk -l
```

Output should have result similar to this. Mainly, here all the disk of the machine is listed. From this we got the name of the USB disk which is `/dev/sda`

![](https://cdn.hashnode.com/res/hashnode/image/upload/v1719385930413/e4ab9a54-f4cc-42ff-9a85-e7195214b68b.png align="center")

Now we'll format the USB but before that we have to unmount the USB. Unmounting ensures that no data is being read from or written to the drive, which helps prevent data corruption and ensures the formatting process can proceed without issues. We can unmount using this command.

```bash
umount /dev/sda*
```

Now to format the USB type this command.

```bash
sudo mkfs.ext4 /dev/sda
        ^            ^
        |            |
   (fileformat) (disk name)
```

![](https://cdn.hashnode.com/res/hashnode/image/upload/v1719388196752/4b12f43b-3981-48b6-abe0-aa0fb9880bc9.png align="center")

After formatting the USB now its time to extract the iso image into USB. For that we'll use `dd` command in linux.

Format for this command `sudo dd if=abc.iso of=usb_disk status='progress'`

`if` = input file (iso image)

`of` = output file (USB disk)

`status='progress'` = to view the progress of the operation

```bash
sudo dd if=pop-os_22.04_amd64_intel_41.iso of=/dev/sda status='progress'
```

change the iso file name and output disk according to your machine.

Thank you for reading, hope it helped you.