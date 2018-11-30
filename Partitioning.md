# Partitioning Your Mac
---

## Purpose of partitioning

The goal of partitioning your HDD/SSD is to create a defined space where your Linux OS will live. Both your Linux OS and MacOS are stored on the same drive but they each exist inside their own container, otherwise known as their "partition".  

## Partitioning with Disk Utility
![](images/dutillogo.png)

Go ahead and open up Disk Utility located in /Applications/Utilities.

Next, you need to select your Mac's main drive then click on the button that says "Partition"

![](images/dutil1.png)

Next, you should see a prompt asking you if you'd like to create an APFS Volume or legitemately partition your drive.  Click "Partition".

![](images/dutil2.png)

After that, you should see a pie chart that shows your drive's partitions.  Assuming you have no other partitions on your system, the pie chart should be completely filled in.  Click on the "+" below the pie chart.

![](images/dutil3.png)

Once you've clicked the "+" you'll notice you now have a new adjustable partition in your pie chart. Adjust the size of this partition to the  amount of storage you wish to give your Linux OS.  I recommend a minimum of 25 GB as the Linux system files will take a significant chunk of this storage.

Next, where it says "Format:" you need to select MS-DOS (FAT)

Then you can name the partition whatever you want and click "Apply"

![](images/dutil4.png)

### Did it work?

If everything worked fine and you received no errors then you are ready to move on to the next step.  However, if you're like me this process did not go as planned then please read the rest of this page.

## Understanding and Troubleshooting APFS
