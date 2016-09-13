 # QC_Jtag_Flash_General

- This Page Describes How to Flash Qualcomm Fluid or MDP 
  QSEE Jtag Flash 

##  Contents
 - Before Starting Please note
 - Download and prepare directory for
 - Download and prepare directory for flashing 
 - Prepare the device to flash
 - Hardware Tools

## Before Starting Please note:
----------------------------

-   The Flashing is on Windows 
-   Software: You need the following: 
    -   OUT directory from Android Compilation 
    -   Download all HK and HY directories from Qualcomm Docs&Downloads
    -   Trace32 installed on your computer (with specific definitions) -
        see [here](http://172.16.7.200/CP/PS/TOOLS/TRACE32)
    -   Python 2.7 (Wasn't tested with later version) 
    -   Note: put python and fastboot apps in windows PATH,
        http://geekswithblogs.net/renso/archive/2009/10/21/how-to-set-the-windows-path-in-windows-7.aspx
-   Hardware: You need the following: 
    -   Lauterbach (+power adapter, and USB cable) 
    -   MDP or SURF 
    -   Debug Board if flashing an MDP (+power adapter and USB cable)

## Download and prepare directory for flashing: 
--------------------------------------------

-   Go to Docs&Downloads site and choose the Platform and build number
    that you want to flash 
    -   Download all **HK** zip files (except for "common", only HY zip
        file should be downloaded) 
    -   Download **HY** zip files with the "boot\_images" and
        "common" folders. (common is the directory inside the zip file,
        most of the time, the zip that located in the root list of the
        files on the site is the common zip )
    -   NOTE: All HK and HY zip files located inside the directories

![GitHub Logo](/images/Docs&Downlaods.png)


-   Create a new directory ( it doesn't matter the name of it, in this
    guide it will be called &lt;ROOT&gt; ) 
-   Extract and copy common HY to &lt;ROOT&gt; directory 
-   Extrat and copy boot\_imagres HY to &lt;ROOT&gt; directory 
-   Extract the HK archives (except to boot\_images and common) to the
    &lt;ROOT&gt; directory 
-   NOTE: You may miss some directories for example "modem\_proc" that
    wont be in the docs&downloads  

![GitHub Logo](/images/FilesList.png)

-   After extracting you will have LINUX folder, inside this directory
    you should have "android\\vendor" directory 
    -   You must copy the "out" directory (output from android
        tree compilation) to the LINUX\\android\\ directory.
    -   Make sure the out directory compiled with the correct platform
        name and build number. 
    -   Note: while copy the out directory from linux to windows you may
        have overwrite message, if you do, press overwrite all. 
-   Run the python script ‘update\_common\_info.py’ from common/build.
    This is what you should see at the end of the script: 

![GitHub Logo](/images/python.png)

-   Copy the "boot\_images" folder from the HK archive to the
    &lt;ROOT&gt; directory, and delete/move/rename the existing one (HY)
    and all its content. 

## Prepare the device to flash:
----------------------------

-   See "Hardware Tools" section below to see the Debug board and
    Lauterbach pictures and connections. 
-   MDP only: Connect the MDP to the Debug board 
-   Connect the Lauterbach and the Debug Board/SURF to the power
-   Connect the Lauterbach to the PC (with USB)
-   Optional: Connect the Debug Board/SURF to the PC (with USB)
-   Start fastboot in the MDP/SURF: (keep volume down button during
    power up cycle) 
    -   Disconnect usb cable and power from the MDP/SURF 
    -   Connect the Power cable 
    -   keep volume down button (keep pressing)
    -   Connect the USB cable 
    -   The LCD will stuck on the penguin picture (see picture below to
        see how the connections should look like) 

## Hardware Tools:
---------------

Note: The pictures below is for 8960 but other platforms look similar.

![Github logo](/images/Lauterbach.png)
![Github logo](/images/DebugBoard.png )
![Final.png](/images/Final.png)
