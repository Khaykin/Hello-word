# TRACE32 

This page explains how to install Trace32 (Lauterbach) 

Related project: [J-tag Flash](/QC_Jtag_Flash_General.md)

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

