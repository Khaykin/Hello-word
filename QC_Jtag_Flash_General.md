#  QC_Jtag_Flash_General

- This Page Describes How to Flash Qualcomm Fluid or MDP 
  QSEE Jtag Flash 

##  Contents
 - Before Starting Please note
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
        see in chapter TRACE32
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

## TRACE32 

This chapter explains how to install Trace32 (Lauterbach) 

Trace32 Installation folder: Y:\CP\HWA\Qualcomm\LinuxAndroid\tools\Lauterbach\setup_06-2013\files\bin\

Installation:

-   Start Setup.exe 
-   NEXT 
-   Accept
-   Destination Folder - It is suggested to leave it C:\T32
-   Pick ARM/Cortex configuration 
-   If question asked on Acrobat reader, you dont have to Download it,
    just press no
-   If this is the first time you installing Trace32 leave it on "New
    Installation" 
-   Choose the second option: "ICD in-Circuit...." 

![Github logo](/images/t32_1.png)

-   Choose "USB Interface" 

![Github logo](/images/t32_2.png)

-   Choose "License Key not necessary" 

![Github logo](/images/t32_3.png)

-   Choose the OS 

![Github logo](/images/t32_4.png)

-   Choose "ICD ARM..." 

![Github logo](/images/t32_5a.png)

-   Choose "YES" 

![Github logo](/images/t32_64bit.png)

-   Wait for copy and installlation to complete 
-   Finished transferring all files from - Press ok
-   Next 

![Github logo](/images/t32_6.png)

-   Press "Install" 

![Github logo](/images/t32_7.png)

-   Ready to use with V - Next/OK 
-   Next 
-   Choose "Next" 

![Github logo](/images/t32_env_var.png)

-   Browse and choose "c:\temp" (folder MUST be called at this name) 

![Github logo](/images/t32_8.png)

-   Choose "Normal Size Font" 

![Github logo](/images/t32_9.png)

-   Choose "Standard Language" 

![Github logo](/images/t32_10.png)

-   Choose "Multiple Document..." 

![Github logo](/images/t32_11.png)

-   Choose "No Integration" 

![Github logo](/images/t32_12.png)

-   Next 

![Github logo](/images/t32_13.png)

-   Choose "Common" 

![Github logo](/images/t32_14.png)

-   Choose "Register Later" 

![Github logo](/images/t32_15.png)

-   OK 

![Github logo](/images/t32_16.png)

-   Do you want to view the README file now? - NO 
-   Finish 

![Github logo](/images/t32_17.png)

**IMPORTANT:** In case of using the Trace32 for
Qualcomm J-tag Flash **VERIFY** the following:

-   You have "C:\temp\T32TMP" directory, in case that this directory
    doesn't exist create it manualy.
-   Go To "C:\T32" Directory and search for "t32marm.exe", if you dont
    have this file, copy all files from C:\T32\bin\windows64 to
    "C:\T32\", in case of overwrite any file do, skip.
-   After installation is done, download: [update icdarm_64](http://www.lauterbach.com/cgi-bin/update.pl?file=_icdarm64_win64.zip)
    & [update icdcortex_win64](http://www.lauterbach.com/cgi-bin/update.pl?file=_icdcortex_win64.zip)
    Extract them into C:\T32 


