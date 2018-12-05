## Customizing rEFInd
***

### Removing Unwanted Boot Options

For the sake of clarity, I had my unwanted rEFInd boot options hidden throughout the making of this tutorial.

If I hadn't hidden my unwanted boot options, my rEFInd start up menu would look something like this:

![](images/uglyrefind.png)

These extra boot options are a result of rEFInd detecting all of the APFS volumes on your system.

To remove any unwanted boot options simply highlight the unwanted option and hit the minus key. After this you should be greeted with a prompt that looks like this:

![](images/refindremove.png)

After removing all of your unwanted boot options you should be left with something like this:

![](images/manjrefind.png)
***
### Theming rEFInd

This will be just a brief introduction to theming rEFInd. For more information, please refer to rEFInd's official documentation bellow:

[Theming rEFInd](https://www.rodsbooks.com/refind/themes.html)

#### Acessing refind.conf

To adjust the appearance of rEFInd we first need to mount our EFI partition.

To mount your EFI partition please refer to the ["Mounting Your EFI Partition" section on the previous page](bootlinux.md#efi123).
