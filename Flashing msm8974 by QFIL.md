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
    flashing](http://172.16.7.200/CP/PS/DEVICES/QC_Build_And_Flash)
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
-   ![GitHub Logo](/images/qfil9872_usb_connector.jpg)
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
-   **Note**:If Device Manager does not recognize as
    described above, please install drivers as described in part
    "Drivers for Qualcomm devices" 

 ## Using QFIL 

<span id="line-81" class="anchor"></span><span id="line-82"
class="anchor"></span><span id="line-83" class="anchor"></span>
-   Start QFIL <span id="line-84" class="anchor"></span><span
    id="line-85" class="anchor"></span><span id="line-86"
    class="anchor"></span>
-   ![GitHub Logo](/images/qfil8974_openqfil.png)
    <span id="line-87" class="anchor"></span><span id="line-88"
    class="anchor"></span><span id="line-89" class="anchor"></span>
-   1st step Before using check up version: click **Help** and after
    **about** <span id="line-90" class="anchor"></span><span
    id="line-91" class="anchor"></span><span id="line-92"
    class="anchor"></span>
-   ![GitHub Logo](/images/qfil8974_15.png)
    <span id="line-93" class="anchor"></span><span id="line-94"
    class="anchor"></span><span id="line-95" class="anchor"></span>
-   Can see the version: <span id="line-96" class="anchor"></span><span
    id="line-97" class="anchor"></span>
-   ![GitHub Logo](/images/qfil8974_14.png)
    <span id="line-98" class="anchor"></span><span id="line-99"
    class="anchor"></span>
-   If version is less than 2.0.0.5, need to install newer QPST version
    as described in part "QPST installation" <span id="line-100"
    class="anchor"></span><span id="line-101" class="anchor"></span>
-   Click &lt;Tools&gt; <span id="line-102" class="anchor"></span><span
    id="line-103" class="anchor"></span>
-   Choose &lt;Flat Meta Build&gt; <span id="line-104"
    class="anchor"></span><span id="line-105" class="anchor"></span>
-   In pop-up window select: Product flavor = asic, Device type=eMMC
    <span id="line-106" class="anchor"></span><span id="line-107"
    class="anchor"></span>
-   Browse for &lt;contents.xml&gt; should be located in root directory
    of prepared image and Flat Build Path, directory where will flatten
    all needed for flashing files. <span id="line-108"
    class="anchor"></span><span id="line-109"
    class="anchor"></span><span id="line-110" class="anchor"></span>

    -   ![GitHub Logo](/images/qfil8974_contents_xml.png)
        <span id="line-111" class="anchor"></span><span id="line-112"
        class="anchor"></span><span id="line-113"
        class="anchor"></span><span id="line-114" class="anchor"></span>
    -   ![GitHub Logo](/images/qfil8974_11.png)
        <span id="line-115" class="anchor"></span><span id="line-116"
        class="anchor"></span><span id="line-117" class="anchor"></span>
-   Click OK, than finished in Status bar will received notification
    "Flatten Succeed" <span id="line-118" class="anchor"></span><span
    id="line-119" class="anchor"></span>
-   Select Build Type: **Flat Build** <span id="line-120"
    class="anchor"></span><span id="line-121" class="anchor"></span>
-   Than started **QFIL** in window shown notification (marked in red)
    <span id="line-122" class="anchor"></span><span id="line-123"
    class="anchor"></span>

    -   ![GitHub Logo](/images/qfil8974_selectport.png)
        <span id="line-124" class="anchor"></span><span id="line-125"
        class="anchor"></span>
-   Choose in **Select Port** needed Target Device, **QFIL** should
    recognize connected device as you can see in the picture below –
    please see red mark in the picture <span id="line-126"
    class="anchor"></span><span id="line-127" class="anchor"></span>

    -   ![GitHub Logo](/images/qfil8974_12.png)
        <span id="line-128" class="anchor"></span><span id="line-129"
        class="anchor"></span>
-   ![{i}](/moin_static194/modernized/img/icon-info.png "{i}"){width="16"
    height="16"} **Note**:If after **Select Port** choosing received:
    **NO PORT AVAILABLE** message =&gt;&gt;&gt; **QFIL** cannot
    recognize the connected device and need to check if driver is
    installed correctly or try to force device to enter EDL using
    debug board. <span id="line-130" class="anchor"></span><span
    id="line-131" class="anchor"></span>

    -   ![GitHub Logo](/images/qfil8974_noport.png)
        <span id="line-132" class="anchor"></span><span id="line-133"
        class="anchor"></span>
-   Select Programmer: Path to &lt;prog\_emmc\_firehose.mbn&gt;
    (for e.g.
    &lt;ROOT&gt;\\8974\_1039.1\\boot\_images\\build\\ms\\bin\\8974\\prog\_emmc\_firehose\_8974.mbn)
    <span id="line-134" class="anchor"></span><span id="line-135"
    class="anchor"></span>
-   Select Build: Path to Flatten Meta Build (was performed above).
    <span id="line-136" class="anchor"></span><span id="line-137"
    class="anchor"></span><span id="line-138" class="anchor"></span>
-   Click on **Load XML** choose path to rawprogram\_unsparse.xml &
    patch0.xml <span id="line-139" class="anchor"></span><span
    id="line-140" class="anchor"></span>
-   Click on **Download** <span id="line-141"
    class="anchor"></span><span id="line-142" class="anchor"></span>
-   In Status bar shown downloading progress <span id="line-143"
    class="anchor"></span><span id="line-144"
    class="anchor"></span><span id="line-145" class="anchor"></span>
-   When downloading (flashing) finished, have notification in Status
    bar <span id="line-146" class="anchor"></span><span id="line-147"
    class="anchor"></span><span id="line-148" class="anchor"></span>
    -   ![GitHub Logo](/images/qfil8974_13.png)
        <span id="line-149" class="anchor"></span><span id="line-150"
        class="anchor"></span><span id="line-151" class="anchor"></span>
-   Reboot Device by disconnect of battery, should start Android OS
    <span id="line-152" class="anchor"></span><span id="line-153"
    class="anchor"></span><span id="line-154" class="anchor"></span>
    -   ![{i}](/moin_static194/modernized/img/icon-info.png "{i}"){width="16"
        height="16"} **Note**: When finishing QFIL burning, need to
        close QFIL SW and not to try to burn device again. <span
        id="line-155" class="anchor"></span><span id="line-156"
        class="anchor"></span><span id="line-157"
        class="anchor"></span><span id="line-158" class="anchor"></span>

        ![{i}](/moin_static194/modernized/img/icon-info.png "{i}"){width="16"
        height="16"} **Note**: Some images will require enabling battery
        charging after flashing: <span id="line-159"
        class="anchor"></span><span id="line-160"
        class="anchor"></span><span id="line-161" class="anchor"></span>

<span id="line-162" class="anchor"></span><span id="line-163"
class="anchor"></span><span id="line-164" class="anchor"></span><span
id="line-165" class="anchor"></span><span id="line-1-1"
class="anchor"></span>

<div class="highlight bash">

<div class="codearea" dir="ltr" lang="en">

``` {#CA-c0d7a62182e0709d71704b95255f4bc798237915 dir="ltr" lang="en"}
   adb root
   adb shell setprop persist.usb.chgdisabled 0
   adb sync
```

</div>

</div>

<span id="line-166" class="anchor"></span><span id="line-167"
class="anchor"></span><span id="line-168" class="anchor"></span><span
id="line-169" class="anchor"></span><span id="line-170"
class="anchor"></span><span id="line-171" class="anchor"></span>

QPST installation: {#QPST_installation:}
------------------

<span id="line-172" class="anchor"></span><span id="line-173"
class="anchor"></span><span id="line-174" class="anchor"></span>
-   Choose and copy to Local PC the latest version of Installer found on
    \\\\qnap\\shared\\CP\\HWA\\Qualcomm\\[LinuxAndroid](/LinuxAndroid){.nonexistent}\\qpst
    (for example: QPST.WIN.2.7 Installer-00438.3). <span id="line-175"
    class="anchor"></span><span id="line-176" class="anchor"></span>
-   After unzip, run **setup.exe**. <span id="line-177"
    class="anchor"></span><span id="line-178" class="anchor"></span>
-   Follow the instructions provided by the installer. This could
    include additional reboots depending on your operating system
    version and that of certain system files that QPST may need
    to update. <span id="line-179" class="anchor"></span><span
    id="line-180" class="anchor"></span>
-   After rebooting the computer, relaunch the setup program by
    double-clicking the **setup.exe.** When the Setup Complete dialog
    appears, the application will be installed successfully. <span
    id="line-181" class="anchor"></span><span id="line-182"
    class="anchor"></span>
-   Click **Finish** to complete the installation. <span id="line-183"
    class="anchor"></span><span id="line-184" class="anchor"></span>

    -   ![{i}](/moin_static194/modernized/img/icon-info.png "{i}"){width="16"
        height="16"} **Note:**To check up for new version of QPST use
        link <https://createpoint.qti.qualcomm.com/tools/> . If do not
        have access to the CDMATech Support website, register
        for access. <span id="line-185" class="anchor"></span><span
        id="line-186" class="anchor"></span>

        ![{i}](/moin_static194/modernized/img/icon-info.png "{i}"){width="16"
        height="16"} **Note:**For more info check here [QPST
        installation](http://172.16.7.200/CP/PS/TOOLS/QPST){.http} <span
        id="line-187" class="anchor"></span><span id="line-188"
        class="anchor"></span><span id="line-189"
        class="anchor"></span><span id="line-190" class="anchor"></span>

Drivers for Qualcomm devices. {#Drivers_for_Qualcomm_devices.}
-----------------------------

<span id="line-191" class="anchor"></span><span id="line-192"
class="anchor"></span>
-   Open Device Manager <span id="line-193" class="anchor"></span><span
    id="line-194" class="anchor"></span>
-   Right mouse click on "Computer" <span id="line-195"
    class="anchor"></span><span id="line-196" class="anchor"></span>
-   Choose "Manage" <span id="line-197" class="anchor"></span><span
    id="line-198" class="anchor"></span>
-   Choose "Device manager" <span id="line-199"
    class="anchor"></span><span id="line-200" class="anchor"></span>
-   Connect the device to the computer <span id="line-201"
    class="anchor"></span><span id="line-202" class="anchor"></span>
-   Now there are several possibilities: <span id="line-203"
    class="anchor"></span><span id="line-204" class="anchor"></span>
-   If you see: **Qualcomm HS-UDB QDLoader 9008** or **Qualcomm HS-USB
    Diagnostics** (skip the driver installation section). <span
    id="line-205" class="anchor"></span><span id="line-206"
    class="anchor"></span><span id="line-207" class="anchor"></span>
-   In case you have **QHSUSB\_DLOAD** <span id="line-208"
    class="anchor"></span><span id="line-209" class="anchor"></span>
-   ![GitHub Logo](/images/qfil8974_1.png)
    <span id="line-210" class="anchor"></span><span id="line-211"
    class="anchor"></span>
-   Install QUD.WIN.1.1 Installer <span id="line-212"
    class="anchor"></span><span id="line-213" class="anchor"></span>
-   Copy QUD.WIN.1.1 Installer-10039.2.zip & MDP.zip from
    \\\\qnap\\shared\\CP\\HWA\\Qualcomm\\[WindowsDrivers](/WindowsDrivers){.nonexistent}
    to &lt; Qualcomm USB Drivers &gt; &lt;Local PC folder&gt; and unzip.
    <span id="line-214" class="anchor"></span><span id="line-215"
    class="anchor"></span>
-   Navigate to &lt;Local PC folder&gt; <span id="line-216"
    class="anchor"></span><span id="line-217" class="anchor"></span>
-   Run **Setup.exe** <span id="line-218" class="anchor"></span><span
    id="line-219" class="anchor"></span>
-   In case you have in &lt;Other devices&gt; can see only
    **&lt;Android&gt;**. <span id="line-220" class="anchor"></span><span
    id="line-221" class="anchor"></span>
-   ![GitHub Logo](/images/qfil8974_2.png)
    <span id="line-222" class="anchor"></span><span id="line-223"
    class="anchor"></span>
-   Install MDP: <span id="line-224" class="anchor"></span><span
    id="line-225" class="anchor"></span>
-   Copy MDP.zip from
    \\\\qnap\\shared\\CP\\HWA\\Qualcomm\\[WindowsDrivers](/WindowsDrivers){.nonexistent}\\MDP.zip
    to &lt;Local PC folder&gt; and unzip <span id="line-226"
    class="anchor"></span><span id="line-227" class="anchor"></span>
-   Open Device Manager <span id="line-228" class="anchor"></span><span
    id="line-229" class="anchor"></span>
-   Right click on &lt;Other Devices&gt; <span id="line-230"
    class="anchor"></span><span id="line-231" class="anchor"></span>
-   Choose &lt;Update Driver Software&gt; <span id="line-232"
    class="anchor"></span><span id="line-233" class="anchor"></span>
-   Choose &lt;Locate and driver software install manually&gt; <span
    id="line-234" class="anchor"></span><span id="line-235"
    class="anchor"></span>

    -   ![GitHub Logo](/images/qfil8974_3.png)
        <span id="line-236" class="anchor"></span><span id="line-237"
        class="anchor"></span>
-   Put local path to &lt;Qualcomm USB Drivers\\unziped MDP&gt; <span
    id="line-238" class="anchor"></span><span id="line-239"
    class="anchor"></span>
-   Next, Close. <span id="line-240" class="anchor"></span><span
    id="line-241" class="anchor"></span>
    -   ![GitHub Logo](/images/qfil8974_4.png)
        <span id="line-242" class="anchor"></span><span id="line-243"
        class="anchor"></span>

        -   ![{i}](/moin_static194/modernized/img/icon-info.png "{i}"){width="16"
            height="16"} **Note:**After driver installation, the Device
            Manager should recognize device as: **Qualcomm HS-UDB
            QDLoader 9008** or **Qualcomm HS-USB Diagnostics**. If
            device manager cannot recognize it as one of these modes,
            please use Debug board in order to force device to enter EDL
            mode as described in part "Using debug board". <span
            id="line-244" class="anchor"></span><span id="line-245"
            class="anchor"></span><span id="line-246"
            class="anchor"></span><span id="line-247"
            class="anchor"></span><span id="line-248"
            class="anchor"></span>

Using Debug Board {#Using_Debug_Board}
-----------------

<span id="line-249" class="anchor"></span><span id="line-250"
class="anchor"></span>
-   Each device may have different debug board (for example:
    msm8960, msm8974) <span id="line-251" class="anchor"></span><span
    id="line-252" class="anchor"></span>
-   ![GitHub Logo](/images/qfil8974_8.jpg)
    <span id="line-253" class="anchor"></span><span id="line-254"
    class="anchor"></span>
-   Force Target Device to enter EDL mode on the debug board: make DIP
    Switch 3 and 5 ON <span id="line-255" class="anchor"></span><span
    id="line-256" class="anchor"></span>
-   ![GitHub Logo](/images/qfil8974_9.jpg)
    <span id="line-257" class="anchor"></span><span id="line-258"
    class="anchor"></span>
-   Place the device on the debug board with no battery by connecting
    connectors: <span id="line-259" class="anchor"></span><span
    id="line-260" class="anchor"></span>
    -   ![GitHub Logo](/images/qfil8974_16.jpg)
        <span id="line-261" class="anchor"></span><span id="line-262"
        class="anchor"></span><span id="line-263"
        class="anchor"></span><span id="line-264" class="anchor"></span>
    -   ![GitHub Logo](/images/qfil8974_17.jpg)
        <span id="line-265" class="anchor"></span><span id="line-266"
        class="anchor"></span><span id="line-267" class="anchor"></span>
-   Connect the debug board to power power adapter (12V, 5.0A) <span
    id="line-268" class="anchor"></span><span id="line-269"
    class="anchor"></span>
    -   ![GitHub Logo](/images/qfil8974_18.jpg)
        <span id="line-270" class="anchor"></span><span id="line-271"
        class="anchor"></span>
-   Connect USB cabel from PC to the device <span id="line-272"
    class="anchor"></span><span id="line-273" class="anchor"></span>
-   Start QFIL (see part "Using QFIL") <span id="line-274"
    class="anchor"></span><span id="line-275" class="anchor"></span>
-   After flashing image, reboot the device by disconnecting Target
    Device from board or on the debug board make DIP Switch 3 to OFF and
    press power on button <span id="line-276"
    class="anchor"></span><span id="line-277" class="anchor"></span>
-   ![GitHub Logo](/images/qfil8974_10.jpg)
    <span id="line-278" class="anchor"></span><span id="line-279"
    class="anchor"></span>
-   The device should start Android OS. <span id="line-280"
    class="anchor"></span>

<span id="bottom" class="anchor"></span>

</div>

<div id="pagebottom">

</div>

</div>

<div id="footer">

-   [MoinMoin
    Powered](http://moinmo.in/ "This site uses the MoinMoin Wiki software.")
-   [Python
    Powered](http://moinmo.in/Python "MoinMoin is written in Python.")
-   [GPL licensed](http://moinmo.in/GPL "MoinMoin is GPL licensed.")
-   [Valid HTML
    4.01](http://validator.w3.org/check?uri=referer "Click here to validate this page.")

</div>
