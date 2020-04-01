# PC-DOS and MS-DOS Installation Guide

This guide explains how to boot regular IBM PC-DOS or Microsoft MS-DOS in DOSBox-X, including creating hard disk images.

Before going through this guide, consider if you really need this as the integrated DOS functionality in DOSBox-X is more convenient for typical use-cases. Booting regular DOS is normally not necessary to run DOS applications such as games, or even Windows version up to 3.11 in DOSBox-X. And even if you have a application that requires a specific DOS version, you can change the reported version of the integrated DOS in DOSBox-X with the ``VER`` command (e.g. ``VER SET 6 22`` will cause DOSBox-X to claim to be version 6.22, instead of the default 5.00).

Some disadvantages of booting regular DOS in DOSBox-X includes:
- Inability to use the ``MOUNT`` command to access directories on the host filesystem. All storage will have to be in the form of images.
- If you need to access a CD-ROM you need to load a driver
- If you need a mouse, you need to load a driver
- Less free memory in the lower 640KB range, and having to tune available memory by selectively loading drivers high.

## General guidelines
This document assumes that you have PC-DOS or MS-DOS disk images. Getting these images files is outside the scope of this document.

### DOS versions
Unless noted otherwise, the PC-DOS and MS-DOS versions are equivalent for this document. There are various limitations that DOS imposes that are dependant on the version. A few milestones:

- PC-DOS version 1.0, supports only diskettes, and only up to 160kB
- MS-DOS version 1.25, first version available to other OEMs
- DOS version 2.0
  - First to support HDDs, capacity dependent on the vendor version (normally 16MB, sometimes 32MB with vendor specific tools)
  - First to support 5.25" 180KB (SSDD) and 360KB disks (DSDD)
- DOS version 3.0
  - First version to support FAT16 partitions up to 32MB
  - First version to support 5.25" 1.2MB disks (HD)
- DOS version 3.2 first version to support 3.5" 720kB disks (2DD)
- DOS version 3.3
  - First version to support extended and logical partitions
  - First version to support HDDs up to 504MB
  - First version to support 3.5" 1.44MB disks (HD)
- PC-DOS version 4.0 was limited to 4 partitions of 1024MB each
- MS-DOS version 4.0
  - First version to allow HDDs up to 4,095MB with up to two partitions (primary of up to 2,047MB and a logical of up to 2,039MB)
  - First version to included HIMEM.SYS XMS 2.x driver with support for up to 16MB RAM
- MS-DOS version 5.0
  - First version to support 3.5" 2.88MB disks (ED)
  - First version to support HDDs up to 7.84GB
- MS-DOS version 6.0 included an updated HIMEM.SYS XMS 3.x driver with support for up to 64MB RAM
- MS-DOS version 7.0 (as part of Windows 95 and 95A)
  - First version to support VFAT
  - First version to allow up to 4GB RAM
  - First version to support LBA for HDDs up to 32GB
- MS-DOS version 7.1 (as part of Windows 95 OSR2, 98 and 98SE)
  - First version to support FAT32
  - First version to support LBA for HDDs up to 128GB (Windows 98 and 98SE only)

### DOS editions
MS-DOS was licensed by many clone manufacturers and in the early days these OEM editions were often 'personalized' to the manufacturer, and therefore it is possible that these older OEM specific editions don't work in DOSBox-X. An example is the Tandy licensed version of MS-DOS, which will not work unless you set ``machine=tandy``.

## Booting DOS from disks
Booting DOS from a disk image is pretty straight forward. Start DOSBox-X and you should find yourself at the DOSBox-X ``Z:\>`` prompt. This is not real DOS, but a 'simulated' DOS that is compatible with most DOS games and applications. Now type something equivalent to
```
 BOOT dos.img
```
Assuming that dos.img is an uncompressed DOS disk image in your current working directory, it should start it. This even works for IBM PC-DOS 1.00.
<img src="images/MS-DOS:PC-DOS_1.0.png" width="640" height="400" alt="Booting a PC-DOS 1.00 diskette image"><br>
## Creating a DOS 2.0 HDD image
TBD...

## Creating a DOS 3.0-3.2 HDD image
First you start DOSBox-X and create an empty HDD image file. Note that due to DOS limitations, the size cannot exceed 31MB, and you can only have a single DOS partition per HDD.

<i>Note:</i> Supposedly the maximum size is 32MB, but anything larger than 31 will fail to boot, this may be a DOSBox-X issue.

<i>Note 2:</i> If you specify a size smaller then 31MB for the IMGMAKE command, pay close attention to the output of IMGMAKE as you will need to adjust the IMGMOUNT size parameter values accordingly.
The IMGMOUNT size parameter should have the format of: ``512,<sectors>,<heads>,<cylinders>``.
```
 IMGMAKE hdd.img -t hd -size 31 -nofs
 IMGMOUNT 2 hdd.img -t hdd -size 512,32,2,992 -fs none
```
<img src="images/MS-DOS:PC-DOS_3.2_IMGMAKE.png" width="640" height="400" alt="Running IMGMAKE and IMGMOUNT commands"><br>

You are now ready to boot the DOS diskette image:
```
 BOOT dos.img
```
Assuming that your uncompressed DOS 3.0-3.2 image is named dos.img and in your current working directory, it should boot DOS from the disk image.
<img src="images/MS-DOS:PC-DOS_3.2_BOOT.png" width="640" height="400"><br>
These early DOS versions did not have an installer, so the preparation and installation is a manual process. You need to start with creating partitions.

Run ``FDISK`` and select option 1 to create a new DOS partition, and confirm you want to use the entire fixed disk for DOS.

<img src="images/MS-DOS:PC-DOS_3.2_FDISK.png" width="640" height="400" alt="Running PC-DOS 3.2 FDISK"><br>

<img src="images/MS-DOS:PC-DOS_3.2_FDISK_Restart.png" width="640" height="400" alt="PC-DOS 3.2 FDISK restart confirmation"><br>

After it is finished, press any key and DOS will reboot DOSBox-X and your again at the DOSBox-X ``Z:\>`` prompt. At this point the HDD image is partitioned, but not yet formatted or made bootable, so that is what you need to do next.
```
 IMGMOUNT 2 hdd.img -t hdd -size 512,32,2,992 -fs none
 BOOT dos.img
```
You have now again booted from the disk image, and are ready to format the C: and transfer the system files.
```
 FORMAT C: /S
```
<img src="images/MS-DOS:PC-DOS_3.2_FORMAT.png" width="640" height="400" alt="Running PC-DOS 3.2 FORMAT command"><br>

You can optionally copy over the rest of the diskette contents at this point
```
 MKDIR C:\DOS
 COPY A:\*.* C:\DOS
```
You can also create a ``AUTOEXEC.BAT`` and ``CONFIG.SYS`` on the HDD with the included ``EDLIN`` editor.

From the DOSBox-X menu bar select Main and then select Reset guest system. You are again at the DOSBox-X ``Z:\>`` prompt.

Our setup is now complete and all that is left is how to boot the image normally. From the DOSBox-X ``Z:\>`` prompt this can be accomplished with
```
IMGMOUNT C hdd.img -size 512,32,2,992
BOOT -L C
```
You probably don't want to memorize those last two commands, so do yourself a favour and create yourself a DOSBox-X .conf file and place those commands in the [Autoexec] section of that config file.

## Creating a DOS 3.3 HDD image
Creating a DOS 3.3 HDD image is nearly identical to that of DOS 3.0-3.2 above with a few small notes
- DOSBox-X does not support creating Extended partitions
- The maximum HDD size is now 504MB but since DOSBox-X does not support Extended partitions, you are effectively still limited to 32MB.
- After you have created your image, due to the newer style partition layout, which DOSBox-X can autodetect, you do not have to specify the geometry to mount the image. So your can boot from the HDD image with the following commands instead.

```
IMGMOUNT C hdd.img
BOOT -L C
```


## Creating a PC-DOS 4.0 HDD image
TBD...

## Creating a MS-DOS 4.0x HDD image
First of all, consider if you really, really want to use MS-DOS 4.x as it was considered a very buggy release. If you decide to continue, and you have the choice, do yourself a favour and use the 3.5" version as it will minimize the amount of disk swapping required.

MS-DOS 4.0x on 5.25" media consists of the following six disks
 - Install
 - Select
 - Operating 1
 - Operating 2
 - Operating 3
 - Shell

MS-DOS 4.0x on 3.5" media consists of the following three disks
 - Setup
 - Operating
 - Shell

OEM versions could have additional disks such as a Diagnostic disk.

Starting with MS-DOS 4 the process to create a HDD image with DOSBox-X, should be easier. But unfortunately there is some kind of compatibility issue between DOSBox-X and the MS-DOS 4.0x installer. If you let DOSBox-X create a image that is already partitioned and formatted the MS-DOS 4.0x installer will not offer the option to install to the HDD.

In these examples we still use a 32MB HDD. MS-DOS 4.0x supports HDDs up to 4,095MB split into two partitions of 2,047MB each. Since DOSBox-X supports only HDD images with primary partitions, 2,047MB is our effective maximum HDD size.

### Bare-bones install
If you decide to do just an absolute minimal install, and effectively skip the MS-DOS 4.0x install program, you don't need to worry about the buggy MS-DOS 4.0x installer, and you can take a shortcut.

```
 IMGMAKE hdd.img -t hd -size 32
 IMGMOUNT C hdd.img
```
Now you need to boot from the first MS-DOS 4.0x disk, which is called either Setup or Install depending on the media type.
```
 BOOT SETUP.IMG
```
When at the Welcome screen (3.5" media) or prompted to insert the SELECT disk (5.25" media), simply press ESC instead followed by F3 to drop to the MS-DOS prompt and run the following command:
```
 SYS C:
```
The HDD image is now bootable and you can optionally copy some of the DOS utilities from the diskette to the HDD and create your ``CONFIG.SYS`` and ``AUTOEXEC.BAT``.

### Full install from 3.5" media
First of all the MS-DOS 4.0x installer can corrupt its own installation diskettes, as such you should change the permission of the disk images in the host OS such that the image files are READ-ONLY. In turn DOSBox-X will treat them as if the disks have the write-protect set.

You first need to create a HDD disk image without partition and filesystem and mount it.
```
 IMGMAKE hdd.img -t hd -size 32 -nofs
 IMGMOUNT 2 hdd.img -t hdd -size 512,63,2,520 -fs none
```
If you specify a different size value then 32MB for the IMGMAKE command, pay close attention to the output of IMGMAKE as you will need to adjust the IMGMOUNT size parameter values accordingly.
The IMGMOUNT size parameter should be 512,<sectors>,<heads>,<cylinders>.

During install, the installer will insist on a blank disk to be labelled "SELECT COPY". Unfortunately will it seems the installer should allow to use the B: drive for this purpose this does not seem to work in practice.
```
 IMGMAKE SELECT_COPY.IMG -t fd_720
 BOOT SETUP.IMG SELECT_COPY.IMG
```
For the first stage of the install, you only need to use the Setup and the blank disk (SELECT_COPY).

It is important that you keep track of the order of the disks that you specify on the BOOT line, as you will need to switch between them using either a keyboard shortcut or the "Swap floppy" option on the DOSBox-X menu bar located under the DOS heading. Unfortunately at this point there is no visual indication in DOSBox-X itself, as to which diskette is the current one inserted, you can however look at the DOSBox messages logged to the console if you have it open to see a message as to which disk is currently inserted. When you cycle through them one by one, once you reach the end, you will simply go back to the first.

Note that while the first MS-DOS 4.0x 3.5" disk is labelled "Setup" the installer will actually refer to it as "INSTALL".

Let the installer create the primary partition, and reset the guest system once it asks you to press Ctrl-Alt-Del. You will now be again at the DOSBox-X ``Z:\>`` prompt and you need to mount the images again. There is now a partition, but not yet a filesystem, and as such DOSBox-X's autodetect does not yet work and you still need to fully specify all the parameters again.
```
 IMGMOUNT 2 hdd.img -t hdd -size 512,63,2,520 -fs none
 BOOT SETUP.IMG SELECT_COPY.IMG OPERATING.IMG MSSHELL.IMG
```
Notice how we have now specified all the disks on the BOOT line, plus the SELECT_COPY disk. You need to go through all the installer questions a second time, and again you need to create the backup copy. Once you get to the partition question, select to skip and the install will then ask for the Operating and finally (if you elected to install it) the Shell disk. After this it will ask to reset the computer, so use the Reset guest system option in DOSBox-X to go back to the ``Z:\>`` prompt.

### Full install from 5.25" media
This process is basically the same as for the 3.5" media, but you have more disks and they are labelled differently.

### Booting MS-DOS 4.0x from HDD
Now that you have created a bootable HDD image you can boot it from the DOSBox-X ``Z:\>`` prompt with the following commands:
```
IMGMOUNT C hdd.img
BOOT -l C
```
## Creating a MS-DOS 5.0+ HDD image
TBD...
