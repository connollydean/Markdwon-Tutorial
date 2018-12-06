# Booting Linux
***

## Getting rEFInd To Detect Your Linux Partition

Since you've successfully installed Linux on your partition, you can unplug your USB and reboot your computer and you should see something like this:

![](images/refindscreen.png)

### What The Fedora?!?!

As you can see, rEFInd is not detecting our Linux install.

This is due to the following warning we saw on the previous page:

![](images/efierror.png)

This warning means we didn't map our Linux install to our EFI partition. While it's possible to map this during our Linux install, I find the following alternative method to be easier and more versatile for future Linux installations.

***

## Installing Super Grub2 Disk

Super Grub2 Disk description:

> Super GRUB2 Disk helps you to boot into most any Operating System (OS) even if you cannot boot into it by normal means.

You can think of Super Grub2 as a back up to rEFInd.  Super Grub2 does a much better job at detecting bootable drives on your system and its a great tool to keep around for future troubleshooting.
***
## Option 1: Creating a bootable Super Grub2 live USB drive

First, download the Super Grub2 Disk x86_64 .ISO file from [this link](https://sourceforge.net/projects/supergrub2/files/2.02s10/super_grub2_disk_2.02s10/super_grub2_disk_x86_64_efi_2.02s10.iso/download).

Next, simply follow the same process from the [Creating A Bootable Linux USB Drive page](linuxusb.md), except replace your Linux .ISO file with the Super Grub2 Disk .ISO file.

You can now use this live USB drive to access the Super Grub2 menu any time the USB drive is plugged in.
***
## Option 2: Installing Super Grub2 Drive as a standalone .EFI file

With this method we'll be installing Super Grub2 as a permanent boot option that we can access at any time from the rEFInd start up menu. I recommend this option over the live USB option as I find having Super Grub2 as a permanent boot option to be more useful than a live USB.

First, download the Super Grub2 Disk EFI x86_64 standalone version from [this link](https://sourceforge.net/projects/supergrub2/files/2.02s10/super_grub2_disk_2.02s10/super_grub2_disk_standalone_x86_64_efi_2.02s10.EFI/download).

Next, we need to rename our file to help rEFInd identify the Super Grub2 EFI file as a bootable option.

For me, the original name of the Super Grub2 EFI file was the following:

`super_grub2_disk_standalone_x86_64_efi_2.02s10.EFI`

go ahead and rename this file to something like this:

`supergrub2_x64.EFI`

It doesn't matter what you name it, it just needs to end with `_x64.EFI`

## Mounting Your EFI Partition<a name="efi123"></a>

To install the Super Grub2 EFI file we need to move it to the EFI partition.

To do this, we need to open up Terminal and find the location of our EFI partition.  To do this type the following command:

`diskutil list`

And you should see something like this:

![](images/efipart.png)

Find the partition thats named "EFI" and take note of the identifier. In my case, its "disk0s1".

Next, we need to mount this partition so we can add our Super Grub2 EFI file to it. To mount the partition, type the following command:

`sudo diskutil mount disk0s1`

You should see something like this in your terminal window:

> Connollys-MBP:~ connollydean$ sudo diskutil mount disk0s1   
Password:   
Volume EFI on disk0s1 mounted

Next, if you open up Finder, you may notice a new drive has appeared named "EFI" like so:

![](images/efifinder.png)

If you don't see this, try pressing `Command + Shift + G` and type "/Volumes/EFI/" like so:

![](images/efifind.png)

You should now be inside the EFI partition which should look like this:

![](images/pregrub.png)

Next, simply drag and drop the Super Grub EFI file inside this directory like so:

![](images/aftergrub.png)

If you did everything correctly, reboot your computer and you should see something like this:

![](images/grubrefind.png)
***

### Booting Youd Linux OS Using Super Grub2 Disk

Now that we have Super Grub2 Disk working we can use it to boot into our Linux OS. Be sure to keep your USB drive disconnected to avoid confusion.

First, boot into Super Grub2 by pressing enter while Super Grub2 is selected in the rEFInd start up menu. You should now see something like this:

![](images/supergrub1.png)

Next, use the arrow keys to select "Detect and show boot methods" and press enter. You should now see something like this:

![](images/supergrub2.png)

On this page, we need to find our Linux OS. As you can see our first two items on the list are labelled "Linux" like so:

> Linux /boot/vmlinuz-4.19-x86_64 (hd5,gpt3)    
Linux /boot/vmlinuz-4.19-x86_64 (single) (hd5,gpt3)

You want to select the one that does NOT say "(single)".  Don't worry if you select the wrong one as you can always reboot and make the correct selection.

Once you have the correct item selected, hit enter to boot into your Linux OS.
***
### Installing rEFInd On Your Linux OS

Now that you've booted into your Linux OS we can go ahead and install rEFInd again within our Linux OS.

Since I'm using Manjaro Linux, this what my booted OS looks like:

![](images/manjscsht.png)

You now need to configure your internet connection and apply any updates your OS may require.  This tutorial will not provide information on how to do this as the process will be different for your specific Linux distribution.  However, WiFi should work out of the box for most popular Linux distros.

First, download the latest version of rEFInd from [this link](https://sourceforge.net/projects/refind/) and navigate to where the folder was downloaded like so:

![](images/manjrefindDL.png)

Next we need to open up the terminal and access the directory where rEFInd is stored using the `cd` command.

For me, rEFInd is stored in the following directory - `/home/connollydean/Downloads/refind-bin-0.11.4`

To access this directory in the terminal we need to use the following command:

`cd /home/connollydean/Downloads/refind-bin-0.11.4`

To view the files within this directory we can use the `ls` command.

Finally, we need to run the "refind-install" file using the following command:

`sudo ./refind-install`

Type your password and hit enter.  If you did everything correctly, your terminal window should look something like this:

![](images/manjterminal.png)

Now that you've installed rEFInd within your Linux OS, the rEFInd start up menu should now display your bootable Linux partition. The rEFInd menu should now look something like this:

![](images/manjrefind.png)
***
### Congratulations! You Now Have A Dual Booting Linux/Mac System!

Now that rEFInd is detecting your bootable Linux partition you can now select your desired OS every time your computer starts up.

If you're satisfied with this you have now completed this tutorial. Otherwise feel free to move on to the "Finishing Touches" page.

***

## [Next Page: Customizing rEFInd](finaltouches.md)

## [Back To Home](README.MD)
