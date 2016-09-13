<div id="header">

<div>

Search:

</div>

<div id="logo">

[![MoinMoin Logo](/moin_static194/common/moinmoin.png)](/FrontPage)

</div>

<span id="pagelocation"><span class="pagepath">[CP](/CP)<span class="sep">/</span>[PRODUCTS](/CP/PRODUCTS)<span class="sep">/</span>[HA](/CP/PRODUCTS/HA)<span class="sep">/</span>[KB](/CP/PRODUCTS/HA/KB){.nonexistent}<span class="sep">/</span>[Partners](/CP/PRODUCTS/HA/KB/Partners){.nonexistent}<span class="sep">/</span>[Qualcomm](/CP/PRODUCTS/HA/KB/Partners/Qualcomm)</span><span class="sep">/</span>[QFIL Flash msm8974](/CP/PRODUCTS/HA/KB/Partners/Qualcomm/QFIL%20Flash%20msm8974?action=fullsearch&value=linkto%3A%22CP%2FPRODUCTS%2FHA%2FKB%2FPartners%2FQualcomm%2FQFIL+Flash+msm8974%22&context=180 "Click to do a full-text search for this title"){.backlink}</span> {#locationline}
============================================================================================================================================================================================================================================================================================================================================================================================================================================================================================================================================================================================================================================================================================

-   [RecentChanges](/RecentChanges)
-   [FindPage](/FindPage)
-   [HelpContents](/HelpContents)
-   [QFIL Flash
    msm8974](/CP/PRODUCTS/HA/KB/Partners/Qualcomm/QFIL%20Flash%20msm8974)

<div id="pageline">

------------------------------------------------------------------------

</div>

</div>

<div id="page" lang="en" dir="ltr">

<div id="content" dir="ltr" lang="en">

<span id="top" class="anchor"></span> <span id="line-1"
class="anchor"></span>

QFIL Flash msm8974 {#QFIL_Flash_msm8974}
==================

<span id="line-2" class="anchor"></span><span id="line-3"
class="anchor"></span>

<div class="table-of-contents">

Contents

1.  [QFIL Flash msm8974](#QFIL_Flash_msm8974)
    1.  [QFIL introduction:](#QFIL_introduction:)
    2.  [Requirements:](#Requirements:)
    3.  [Target Device State](#Target_Device_State)
    4.  [Using QFIL](#Using_QFIL)
    5.  [QPST installation:](#QPST_installation:)
    6.  [Drivers for Qualcomm devices.](#Drivers_for_Qualcomm_devices.)
    7.  [Using Debug Board](#Using_Debug_Board)

</div>

<span id="line-4" class="anchor"></span><span id="line-5"
class="anchor"></span><span id="line-6" class="anchor"></span><span
id="line-7" class="anchor"></span>

QFIL introduction: {#QFIL_introduction:}
------------------

<span id="line-8" class="anchor"></span>
· The Qualcomm Flash Image Loader (QFIL) is software which is integrated
in Qualcomm Product Support Tool (QPST™) used to flash a build image
into a Target Device in Emergency Download (EDL) mode or High Level OS
(HLOS) mode (normal Android Bootup). <span id="line-9"
class="anchor"></span><span id="line-10" class="anchor"></span>

· This tool can recover devices that are in a bad state and cannot be
flashed using J-TAG (i.e., do not have J-TAG port enabled, e.g.,
Bsquare, Intrisyc devices). <span id="line-11"
class="anchor"></span><span id="line-12" class="anchor"></span>

. QFIL have 2 possible options to flash Images: <span id="line-13"
class="anchor"></span><span id="line-14" class="anchor"></span>

-   By connecting Target Device to the Windows PC using USB cable as
    described in part "Using QFIL" <span id="line-15"
    class="anchor"></span><span id="line-16" class="anchor"></span>
-   By connecting Target Device to the Windows PC using debug board as
    described in part "Using Debug Board". Debug board needed, if Target
    Device not recognized by PC, see part bellow "Drivers for Qualcomm
    devices" <span id="line-17" class="anchor"></span><span id="line-18"
    class="anchor"></span>

. ![{i}](/moin_static194/modernized/img/icon-info.png "{i}"){width="16"
height="16"} **NOTE**: QFIL automatically switches the Target Device to
EDL mode and then flash the build image to the device <span id="line-19"
class="anchor"></span><span id="line-20" class="anchor"></span>

-   ![7.png](/CP/PRODUCTS/HA/KB/Partners/Qualcomm/QFIL%20Flash%20msm8974?action=AttachFile&do=get&target=7.png "7.png"){.attachment}
    <span id="line-21" class="anchor"></span><span id="line-22"
    class="anchor"></span><span id="line-23" class="anchor"></span><span
    id="line-24" class="anchor"></span>

Requirements: {#Requirements:}
-------------

<span id="line-25" class="anchor"></span>
-   Windows PC <span id="line-26" class="anchor"></span><span
    id="line-27" class="anchor"></span>
-   Target device <span id="line-28" class="anchor"></span><span
    id="line-29" class="anchor"></span>
-   USB Cable <span id="line-30" class="anchor"></span><span
    id="line-31" class="anchor"></span>
-   Charged battery or Debug board (if needed, see below...) <span
    id="line-32" class="anchor"></span><span id="line-33"
    class="anchor"></span>
-   [Image ready for
    flashing](http://172.16.7.200/CP/PS/DEVICES/QC_Build_And_Flash){.http}
    <span id="line-34" class="anchor"></span><span id="line-35"
    class="anchor"></span>
-   ![{i}](/moin_static194/modernized/img/icon-info.png "{i}"){width="16"
    height="16"} **Note**: Before flashing image must invoke
    “update\_common\_info.py” from location: &lt;repository
    folder&gt;\\common\\build (need to do it only once per image) <span
    id="line-36" class="anchor"></span><span id="line-37"
    class="anchor"></span>
-   QPST software (QFIL is software which integrated in QPST. If don't
    have, install as described in part "QPST installation") <span
    id="line-38" class="anchor"></span><span id="line-39"
    class="anchor"></span>
-   Qualcomm drivers (see part below "Drivers for Qualcomm devices")
    <span id="line-40" class="anchor"></span><span id="line-41"
    class="anchor"></span>
-   [Installed Android
    SDK](http://developer.android.com/intl/ru/sdk/installing/index.html?pkg=tools){.http}
    <span id="line-42" class="anchor"></span><span id="line-43"
    class="anchor"></span>
-   Installed Java from 7 and above (needed for SDK) <span id="line-44"
    class="anchor"></span><span id="line-45" class="anchor"></span>
-   Installed Python(x,y) <span id="line-46" class="anchor"></span><span
    id="line-47" class="anchor"></span><span id="line-48"
    class="anchor"></span><span id="line-49" class="anchor"></span>

Target Device State {#Target_Device_State}
-------------------

<span id="line-50" class="anchor"></span><span id="line-51"
class="anchor"></span><span id="line-52" class="anchor"></span>
-   Connect Target device with charged battery by USB cable to Windows
    PC <span id="line-53" class="anchor"></span><span id="line-54"
    class="anchor"></span>
    -   ![usb\_connector.jpg](/CP/PRODUCTS/HA/KB/Partners/Qualcomm/QFIL%20Flash%20msm8974?action=AttachFile&do=get&target=usb_connector.jpg "usb_connector.jpg"){.attachment}
        <span id="line-55" class="anchor"></span><span id="line-56"
        class="anchor"></span>
-   Open Device Manager <span id="line-57" class="anchor"></span><span
    id="line-58" class="anchor"></span>
-   Device Manager should recognize it as: <span id="line-59"
    class="anchor"></span><span id="line-60" class="anchor"></span><span
    id="line-61" class="anchor"></span>
-   If Target Device is in **EDL mode**, the port information will
    displayed on Device Manager **Qualcomm HS-USB QDLoader**. <span
    id="line-62" class="anchor"></span><span id="line-63"
    class="anchor"></span><span id="line-64" class="anchor"></span>

    -   ![edldevman.png](/CP/PRODUCTS/HA/KB/Partners/Qualcomm/QFIL%20Flash%20msm8974?action=AttachFile&do=get&target=edldevman.png "edldevman.png"){.attachment}
        <span id="line-65" class="anchor"></span><span id="line-66"
        class="anchor"></span><span id="line-67" class="anchor"></span>
-   If Target Device boots up with no issues and the HLOS is running, in
    Device Manager will be called as **Qualcomm HS-USB Diagnostics
    9025** . <span id="line-68" class="anchor"></span><span id="line-69"
    class="anchor"></span><span id="line-70" class="anchor"></span>

    -   ![6.png](/CP/PRODUCTS/HA/KB/Partners/Qualcomm/QFIL%20Flash%20msm8974?action=AttachFile&do=get&target=6.png "6.png"){.attachment}
        <span id="line-71" class="anchor"></span><span id="line-72"
        class="anchor"></span>
-   When Target Device is connected to the PC and recognized as Device
    in EDL or diagnostic mode follow to next part "Using QFIL" <span
    id="line-73" class="anchor"></span><span id="line-74"
    class="anchor"></span><span id="line-75" class="anchor"></span>
-   ![{i}](/moin_static194/modernized/img/icon-info.png "{i}"){width="16"
    height="16"} **Note**:If Device Manager does not recognize as
    described above, please install drivers as described in part
    "Drivers for Qualcomm devices" <span id="line-76"
    class="anchor"></span><span id="line-77" class="anchor"></span><span
    id="line-78" class="anchor"></span><span id="line-79"
    class="anchor"></span><span id="line-80" class="anchor"></span>

Using QFIL {#Using_QFIL}
----------

<span id="line-81" class="anchor"></span><span id="line-82"
class="anchor"></span><span id="line-83" class="anchor"></span>
-   Start QFIL <span id="line-84" class="anchor"></span><span
    id="line-85" class="anchor"></span><span id="line-86"
    class="anchor"></span>
-   ![openqfil.png](/CP/PRODUCTS/HA/KB/Partners/Qualcomm/QFIL%20Flash%20msm8974?action=AttachFile&do=get&target=openqfil.png "openqfil.png"){.attachment}
    <span id="line-87" class="anchor"></span><span id="line-88"
    class="anchor"></span><span id="line-89" class="anchor"></span>
-   1st step Before using check up version: click **Help** and after
    **about** <span id="line-90" class="anchor"></span><span
    id="line-91" class="anchor"></span><span id="line-92"
    class="anchor"></span>
-   ![15.png](/CP/PRODUCTS/HA/KB/Partners/Qualcomm/QFIL%20Flash%20msm8974?action=AttachFile&do=get&target=15.png "15.png"){.attachment}
    <span id="line-93" class="anchor"></span><span id="line-94"
    class="anchor"></span><span id="line-95" class="anchor"></span>
-   Can see the version: <span id="line-96" class="anchor"></span><span
    id="line-97" class="anchor"></span>
-   ![14.png](/CP/PRODUCTS/HA/KB/Partners/Qualcomm/QFIL%20Flash%20msm8974?action=AttachFile&do=get&target=14.png "14.png"){.attachment}
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

    -   ![contents\_xml.png](/CP/PRODUCTS/HA/KB/Partners/Qualcomm/QFIL%20Flash%20msm8974?action=AttachFile&do=get&target=contents_xml.png "contents_xml.png"){.attachment}
        <span id="line-111" class="anchor"></span><span id="line-112"
        class="anchor"></span><span id="line-113"
        class="anchor"></span><span id="line-114" class="anchor"></span>
    -   ![11.png](/CP/PRODUCTS/HA/KB/Partners/Qualcomm/QFIL%20Flash%20msm8974?action=AttachFile&do=get&target=11.png "11.png"){.attachment}
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

    -   ![selectport.png](/CP/PRODUCTS/HA/KB/Partners/Qualcomm/QFIL%20Flash%20msm8974?action=AttachFile&do=get&target=selectport.png "selectport.png"){.attachment}
        <span id="line-124" class="anchor"></span><span id="line-125"
        class="anchor"></span>
-   Choose in **Select Port** needed Target Device, **QFIL** should
    recognize connected device as you can see in the picture below –
    please see red mark in the picture <span id="line-126"
    class="anchor"></span><span id="line-127" class="anchor"></span>

    -   ![12.png](/CP/PRODUCTS/HA/KB/Partners/Qualcomm/QFIL%20Flash%20msm8974?action=AttachFile&do=get&target=12.png "12.png"){.attachment}
        <span id="line-128" class="anchor"></span><span id="line-129"
        class="anchor"></span>
-   ![{i}](/moin_static194/modernized/img/icon-info.png "{i}"){width="16"
    height="16"} **Note**:If after **Select Port** choosing received:
    **NO PORT AVAILABLE** message =&gt;&gt;&gt; **QFIL** cannot
    recognize the connected device and need to check if driver is
    installed correctly or try to force device to enter EDL using
    debug board. <span id="line-130" class="anchor"></span><span
    id="line-131" class="anchor"></span>

    -   ![noport.png](/CP/PRODUCTS/HA/KB/Partners/Qualcomm/QFIL%20Flash%20msm8974?action=AttachFile&do=get&target=noport.png "noport.png"){.attachment}
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
    -   ![13.png](/CP/PRODUCTS/HA/KB/Partners/Qualcomm/QFIL%20Flash%20msm8974?action=AttachFile&do=get&target=13.png "13.png"){.attachment}
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
-   ![1.png](/CP/PRODUCTS/HA/KB/Partners/Qualcomm/QFIL%20Flash%20msm8974?action=AttachFile&do=get&target=1.png "1.png"){.attachment}
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
-   ![2.png](/CP/PRODUCTS/HA/KB/Partners/Qualcomm/QFIL%20Flash%20msm8974?action=AttachFile&do=get&target=2.png "2.png"){.attachment}
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

    -   ![3.png](/CP/PRODUCTS/HA/KB/Partners/Qualcomm/QFIL%20Flash%20msm8974?action=AttachFile&do=get&target=3.png "3.png"){.attachment}
        <span id="line-236" class="anchor"></span><span id="line-237"
        class="anchor"></span>
-   Put local path to &lt;Qualcomm USB Drivers\\unziped MDP&gt; <span
    id="line-238" class="anchor"></span><span id="line-239"
    class="anchor"></span>
-   Next, Close. <span id="line-240" class="anchor"></span><span
    id="line-241" class="anchor"></span>
    -   ![4.png](/CP/PRODUCTS/HA/KB/Partners/Qualcomm/QFIL%20Flash%20msm8974?action=AttachFile&do=get&target=4.png "4.png"){.attachment}
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
-   ![8.jpg](/CP/PRODUCTS/HA/KB/Partners/Qualcomm/QFIL%20Flash%20msm8974?action=AttachFile&do=get&target=8.jpg "8.jpg"){.attachment}
    <span id="line-253" class="anchor"></span><span id="line-254"
    class="anchor"></span>
-   Force Target Device to enter EDL mode on the debug board: make DIP
    Switch 3 and 5 ON <span id="line-255" class="anchor"></span><span
    id="line-256" class="anchor"></span>
-   ![9.jpg](/CP/PRODUCTS/HA/KB/Partners/Qualcomm/QFIL%20Flash%20msm8974?action=AttachFile&do=get&target=9.jpg "9.jpg"){.attachment}
    <span id="line-257" class="anchor"></span><span id="line-258"
    class="anchor"></span>
-   Place the device on the debug board with no battery by connecting
    connectors: <span id="line-259" class="anchor"></span><span
    id="line-260" class="anchor"></span>
    -   ![16.jpg](/CP/PRODUCTS/HA/KB/Partners/Qualcomm/QFIL%20Flash%20msm8974?action=AttachFile&do=get&target=16.jpg "16.jpg"){.attachment}
        <span id="line-261" class="anchor"></span><span id="line-262"
        class="anchor"></span><span id="line-263"
        class="anchor"></span><span id="line-264" class="anchor"></span>
    -   ![17.jpg](/CP/PRODUCTS/HA/KB/Partners/Qualcomm/QFIL%20Flash%20msm8974?action=AttachFile&do=get&target=17.jpg "17.jpg"){.attachment}
        <span id="line-265" class="anchor"></span><span id="line-266"
        class="anchor"></span><span id="line-267" class="anchor"></span>
-   Connect the debug board to power power adapter (12V, 5.0A) <span
    id="line-268" class="anchor"></span><span id="line-269"
    class="anchor"></span>
    -   ![18.jpg](/CP/PRODUCTS/HA/KB/Partners/Qualcomm/QFIL%20Flash%20msm8974?action=AttachFile&do=get&target=18.jpg "18.jpg"){.attachment}
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
-   ![10.jpg](/CP/PRODUCTS/HA/KB/Partners/Qualcomm/QFIL%20Flash%20msm8974?action=AttachFile&do=get&target=10.jpg "10.jpg"){.attachment}
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
