# QFIL Flash msm8974#

## Contents:
    1.  QFIL introduction:
    2.  Requirements
    3.  Target Device State
    4.  Using QFIL
    5.  QPST installation:
    6.  Drivers for Qualcomm devices
    7.  Using Debug Board

## QFIL introduction:
* **The Qualcomm Flash _Image_ Loader (QFIL)** is software which is integrated
in Qualcomm Product Support Tool (QPST™) used to flash a build image
into a Target Device in Emergency Download (EDL) mode or High Level OS
(HLOS) mode (normal Android Bootup). 
* This tool can recover devices that are in a bad state and cannot be
flashed using J-TAG (i.e., do not have J-TAG port enabled, e.g.,
Bsquare, Intrisyc devices). 
* QFIL have 2 possible options to flash Images: 
  -   By connecting Target Device to the Windows PC using USB cable as
    described in part "Using QFIL" 
  *   By connecting Target Device to the Windows PC using debug board as
    described in part "Using Debug Board". Debug board needed, if Target
    Device not recognized by PC, see part bellow "Drivers for Qualcomm
    devices" 

**NOTE:** QFIL automatically switches the Target Device to
EDL mode and then flash the build image to the device. 
-   ![GitHub Logo](/images/qfil8974_7.png)

## Requirements:

-   Windows PC 
-   Target device
-   USB Cable 
-   Charged battery or Debug board (if needed, see below...)
-   [Image ready for
    flashing](/tree/master/docs/internal/QC_Build_And_Flash)
-   **Note:** Before flashing image must invoke
    ''python update\common\info.py' from location: ''repository
    folder\common\build'' (need to do it only once per image)
-   QPST software (QFIL is software which integrated in QPST. If don't
    have, install as described in part "QPST installation"
-   Qualcomm drivers (see part below "Drivers for Qualcomm devices")
-   [Installed Android
    SDK](http://developer.android.com/intl/ru/sdk/installing/index.html?pkg=tools)
-   Installed Java from 7 and above (needed for SDK) 
-   Installed Python(x,y) 

## Target Device State

-   Connect Target device with charged battery by USB cable to Windows
    PC 
   ![GitHub Logo](/images/qfil8974_usb_connector.jpg)
-   Open Device Manager 
-   Device Manager should recognize it as:
-   If Target Device is in **EDL mode**, the port information will
    displayed on Device Manager **Qualcomm HS-USB QDLoader**.    
-   ![GitHub Logo](/images/qfil8974_edldevman.png)
-   If Target Device boots up with no issues and the HLOS is running, in
    Device Manager will be called as **Qualcomm HS-USB Diagnostics
    9025**.
-   ![GitHub Logo](/images/qfil8974_6.png)
-   When Target Device is connected to the PC and recognized as Device
    in EDL or diagnostic mode follow to next part "Using QFIL"
-   **Note:** If Device Manager does not recognize as
    described above, please install drivers as described in part
    "Drivers for Qualcomm devices" 

 ## Using QFIL 

-   Start QFIL
    ![GitHub Logo](/images/qfil8974_openqfil.png)
-   1st step Before using check up version: click **Help** and after
    **about** 
    ![GitHub Logo](/images/qfil8974_15.png)
-   Can see the version: 
    ![GitHub Logo](/images/qfil8974_14.png)
-   If version is less than 2.0.0.5, need to install newer QPST version
    as described in part "QPST installation" 
-   Click: Tools 
-   Choose: Flat Meta Build
-   In pop-up window select: Product flavor = asic, Device type=eMMC
-   Browse: contents.xml should be located in root directory
    of prepared image and Flat Build Path, directory where will flatten
    all needed for flashing files.
    
   ![GitHub Logo](/images/qfil8974_contents_xml.png)
   ![GitHub Logo](/images/qfil8974_11.png)
-   Click OK, than finished in Status bar will received notification
    "Flatten Succeed" 
-   Select Build Type: **Flat Build** 
-   Than started **QFIL** in window shown notification (marked in red)

   ![GitHub Logo](/images/qfil8974_selectport.png)
-   Choose in **Select Port** needed Target Device, **QFIL** should
    recognize connected device as you can see in the picture below –
    please see red mark in the picture 
    ![GitHub Logo](/images/qfil8974_12.png)
-   **Note**:If after **Select Port** choosing received:
    **NO PORT AVAILABLE** message,its **QFIL** cannot
    recognize the connected device and need to check if driver is
    installed correctly or try to force device to enter EDL using
    debug board.

   ![GitHub Logo](/images/qfil8974_noport.png)
-   Select Programmer: "prog_emmc_firehose.mbn";
    (for e.g.
    ROOT\8974_1039.1\boot\_images\build\ms\bin\8974\prog_emmc_firehose_8974.mbn)
-   Select Build: Path to Flatten Meta Build (was performed above).
-   Click on **Load XML** choose path to rawprogram\_unsparse.xml &
    patch0.xml 
-   Click on **Download** 
-   In Status bar shown downloading progress
-   When downloading (flashing) finished, have notification in Status
    bar 
    ![GitHub Logo](/images/qfil8974_13.png)
-   Reboot Device by disconnect of battery, should start Android OS
-   **Note:** When finishing QFIL burning, need to
    close QFIL SW and not to try to burn device again.
-   **Note:** Some images will require enabling battery
    charging after flashing:

 ``` 
  adb root
  adb shell setprop persist.usb.chgdisabled 0
  adb sync
 ```

 ## QPST installation:

-   Choose and copy to Local PC the latest version of Installer found on
    \\qnap\shared\CP\HWA\Qualcomm\LinuxAndroid\qpst
    (for example: QPST.WIN.2.7 Installer-00438.3).
-   After unzip, run **setup.exe**. 
-   Follow the instructions provided by the installer. This could
    include additional reboots depending on your operating system
    version and that of certain system files that QPST may need
    to update. 
-   After rebooting the computer, relaunch the setup program by
    double-clicking the **setup.exe.** When the Setup Complete dialog
    appears, the application will be installed successfully. 
-   Click **Finish** to complete the installation.

-   **Note:** To check up for new version of QPST use
    link <https://createpoint.qti.qualcomm.com/tools/> . If do not
    have access to the CDMATech Support website, register
    for access.

 ## Drivers for Qualcomm devices.

-   Open Device Manager
-   Right mouse click on "Computer"
-   Choose "Manage" 
-   Choose "Device manager"
-   Connect the device to the computer
-   Now there are several possibilities:
-   If you see: **Qualcomm HS-UDB QDLoader 9008** or **Qualcomm HS-USB
    Diagnostics** (skip the driver installation section). 
-   In case you have **QHSUSB\_DLOAD** r"></span>
    ![GitHub Logo](/images/qfil8974_1.png)
-   Install QUD.WIN.1.1 Installer 
-   Copy QUD.WIN.1.1 Installer-10039.2.zip & MDP.zip from
    \\qnap\shared\CP\HWA\Qualcomm\WindowsDrivers to Local PC folder.
-   Navigate to Local PC folder; and unzip folder contents. 
-   Run **Setup.exe** 
-   In case you have in Other devices can see only
    **Android**.
-   ![GitHub Logo](/images/qfil8974_2.png)
-   Install MDP: 
-   Copy MDP.zip from
    \\qnap\shared\CP\HWA\Qualcomm\WindowsDrivers\MDP.zip
    to Local PC folder;and unzip
-   Open Device Manager 
-   Right click on **Other Devices**
-   Choose **Update Driver Software**
-   Choose **Locate and driver software install manually**
-   ![GitHub Logo](/images/qfil8974_3.png)
-   Put local path to Qualcomm USB Drivers\unziped MDP
-   Next, Close. 
-   ![GitHub Logo](/images/qfil8974_4.png)
-   **Note:**After driver installation, the Device
    Manager should recognize device as: **Qualcomm HS-UDB
    QDLoader 9008** or **Qualcomm HS-USB Diagnostics**. If
    device manager cannot recognize it as one of these modes,
    please use Debug board in order to force device to enter EDL
    mode as described in part "Using debug board".

## Using Debug Board 

-   Each device may have different debug board (for example: msm8974)
    ![GitHub Logo](/images/qfil8974_8.jpg)
-   Force Target Device to enter EDL mode on the debug board: make DIP
    Switch 3 and 5 ON
    ![GitHub Logo](/images/qfil8974_9.jpg)
-   Place the device on the debug board with no battery by connecting
    connectors: 
    ![GitHub Logo](/images/qfil8974_16.jpg)
    ![GitHub Logo](/images/qfil8974_17.jpg)
-   Connect the debug board to power power adapter (12V, 5.0A) 
    ![GitHub Logo](/images/qfil8974_18.jpg)
-   Connect USB cabel from PC to the device
-   Start QFIL (see part "Using QFIL") 
-   After flashing image, reboot the device by disconnecting Target
    Device from board or on the debug board make DIP Switch 3 to OFF and
    press power on button 
    ![GitHub Logo](/images/qfil8974_10.jpg)
-   The device should start Android OS. 
