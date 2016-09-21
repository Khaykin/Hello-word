

<span id="line-2" class="anchor"></span>
**![{\*}](/moin_static194/modernized/img/star_on.png "{*}"){width="16"
height="16"} <span class="u">Building the project </span>** <span
id="line-3" class="anchor"></span><span id="line-4"
class="anchor"></span>

#### HLOS {#HLOS}

<span id="line-5" class="anchor"></span>
<span class="u">General</span>: <span id="line-6"
class="anchor"></span><span id="line-7" class="anchor"></span>

-   Makefile in use: Application.mk and Androind.mk under
    \$**HDCP**\_PROJ/jni <span id="line-8" class="anchor"></span>
-   Build directory: \$**HDCP**\_PROJ <span id="line-9"
    class="anchor"></span>
-   Build **products** under: libs/armeabi <span id="line-10"
    class="anchor"></span>
-   Pushing **products** to the device: <span id="line-11"
    class="anchor"></span>
    -   adb push libs/armeabi/libDx**Hdcp**.so
        /system/lib/libDx**Hdcp**.so <span id="line-12"
        class="anchor"></span>
    -   adb push external/**HDCP**\_API/Dx**HDCP**.cfg /system/etc <span
        id="line-13" class="anchor"></span><span id="line-14"
        class="anchor"></span>

<span class="u">Build command</span>: <span id="line-15"
class="anchor"></span><span id="line-16" class="anchor"></span>

<span id="line-17" class="anchor"></span><span id="line-18"
class="anchor"></span><span id="line-19" class="anchor"></span>

    #ndk-build TZ_PLAT_PATH=$TZ_PLATFORMS_ROOT/Qualcomm RELEASE=yes IGNORE_VERSIONS=no DXINFRA_ROOT=DxInfra WHITE_BOX_TESTS=yes
    #ndk-build TZ_PLAT_PATH=$TZ_PLATFORMS_ROOT/Qualcomm RELEASE=yes SUB_PLAT=AndroidTZ2_0 IGNORE_VERSIONS=no DXINFRA_ROOT=DxInfra WHITE_BOX_TESTS=yes

<span id="line-20" class="anchor"></span>
<span class="u">Clean command</span>: <span id="line-21"
class="anchor"></span><span id="line-22" class="anchor"></span>

<span id="line-23" class="anchor"></span><span id="line-24"
class="anchor"></span><span id="line-25" class="anchor"></span>

    #ndk-build TZ_PLAT_PATH=$TZ_PLATFORMS_ROOT/Qualcomm RELEASE=yes IGNORE_VERSIONS=no DXINFRA_ROOT=DxInfra WHITE_BOX_TESTS=yes clean
    #ndk-build TZ_PLAT_PATH=$TZ_PLATFORMS_ROOT/Qualcomm RELEASE=yes SUB_PLAT=AndroidTZ2_0 IGNORE_VERSIONS=no DXINFRA_ROOT=DxInfra WHITE_BOX_TESTS=yes clean

<span id="line-26" class="anchor"></span>

#### TZ {#TZ}

<span id="line-27" class="anchor"></span>
<span class="u">General</span>: <span id="line-28"
class="anchor"></span><span id="line-29" class="anchor"></span>

-   Makefile Uses the file:
    \$**HDCP**\_PROJ/TZService/Workspace/Qualcomm/Makefile <span
    id="line-30" class="anchor"></span>
-   Build directory: \$**HDCP**\_PROJ/TZService/Workspace/Qualcomm <span
    id="line-31" class="anchor"></span>
-   Build **products** under:
    \$**HDCP**\_PROJ/TZService/Workspace/Qualcomm/trustzone\_ref\_integration
    <span id="line-32" class="anchor"></span>
-   TST vs. PROD: Usually we use the build **products** under TST. The
    build **products** under PROD are used when we work with a dongle
    that has production keys. <span id="line-33" class="anchor"></span>
-   Pushing **products** to the device: Use Push.sh from files
    location -
    [Push.sh](/CP/PRODUCTS/HA/KB/HDCP_Ref_Guide?action=AttachFile&do=view&target=Push.sh){.attachment}
    <span id="line-34" class="anchor"></span><span id="line-35"
    class="anchor"></span>

<span class="u">Build command</span>: <span id="line-36"
class="anchor"></span><span id="line-37" class="anchor"></span>

<span id="line-38" class="anchor"></span><span id="line-39"
class="anchor"></span><span id="line-40" class="anchor"></span><span
id="line-41" class="anchor"></span><span id="line-42"
class="anchor"></span><span id="line-43" class="anchor"></span><span
id="line-44" class="anchor"></span><span id="line-45"
class="anchor"></span>

    #make TZ_PLAT_PATH=$TZ_PLATFORMS_ROOT/Qualcomm PLAT_VER=2330 PLAT=MSM8960Qsee
    #make TZ_PLAT_PATH=$TZ_PLATFORMS_ROOT/Qualcomm PLAT_VER=23210.3 PLAT=MSM8960Qsee
    #make TZ_PLAT_PATH=$TZ_PLATFORMS_ROOT/Qualcomm PLAT_VER=1514 PLAT=MPQ8064Qsee HDMI_STATUS_SUPPORT=no
    #make TZ_PLAT_PATH=$TZ_PLATFORMS_ROOT/Qualcomm PLAT_VER=1021.1 PLAT=MSM8974Qsee HDMI_STATUS_SUPPORT=no
    #make TZ_PLAT_PATH=$TZ_PLATFORMS_ROOT/Qualcomm PLAT_VER=1031.12 PLAT=MSM8974Qsee HDMI_STATUS_SUPPORT=no
    #make TZ_PLAT_PATH=$TZ_PLATFORMS_ROOT/Qualcomm PLAT_VER=1035.1 PLAT=MSM8974Qsee HDMI_STATUS_SUPPORT=no
    #make TZ_PLAT_PATH=$TZ_PLATFORMS_ROOT/Qualcomm PLAT_VER=1039.1 PLAT=MSM8974Qsee HDMI_STATUS_SUPPORT=no

<span id="line-46" class="anchor"></span>
<span class="u">Clean command</span>: <span id="line-47"
class="anchor"></span><span id="line-48" class="anchor"></span>

<span id="line-49" class="anchor"></span><span id="line-50"
class="anchor"></span>

    #make TZ_PLAT_PATH=$TZ_PLATFORMS_ROOT/Qualcomm PLAT_VER=2330 PLAT=MSM8960Qsee clean

## Provisioning

**Step 1:** PC tool (dx**hdcp**prov.exe) installation 
 - If the DxHdcpProvisioning tool is not installed on your machine, you need to:
    - In Visual Studio, build the solution dxhdcpprov.sln under /master/HDCP/tools/dxhdcpprov
    - Run setup.exe under /master/HDCP/tools/Setup/Release
 -  This will install dxhdcpprov.exe and copy 2 dll files (ProvisioningTool.dll and QAT_CryptoEngine2.dll) 
   to C:\Program    Files\Discretix\DxHdcpProvisioning

**Step 2:** Use the PC tool to encrypt secret data 

-  Run->cmd
-  cd C:\Program Files\Discretix\DxHdcpProvisioning\
-  Execute commmands:
-  For Tx: `dxhdcpprov -v -tx -hdcp2_data_file Tx_HDCP2_OrderNo_1_Data.bin -cek HDCP2_Cek.dat -oemid HDCP2_OemId.dat -o PM_Tx.out`
-  For Rx: `dxhdcpprov -v -rx -hdcp2_data_file Rx_HDCP2_OrderNo_1_Data.bin -cek HDCP2_Cek.dat -oemid HDCP2_OemId.dat -o PM_Rx.out`
-  **Note:** bin and dat files can be taken from [ProvisioningTestFiles](/master/HDCP/tools/ProvisioningTestFiles)
-  This will generate PM_Rx.out / PM_Tx.out files which are the encrypted data package files to use in step 2

**Step 2:** Use the encrypted data package + CEK to provision the device

-  In this step we provision the device, which means we decrypt the encrypted data package using CEK, 
   and store the secrest on the  device's SFS.
-  There are 2 alternative options for this step:
    - Use DxProvTst tool:
      - When building the HDCP project, DxProvTst will be generated under /HDCP/libs/armeabi/
    - Push the below to the device (all to the same directory, doesn't matter which one):
      * DxProvTst
      * CEK file used in previous steps
      * PM.out file used in previous steps
      * Rename the CEK and PM file to match the hardcoded names under /HDCP/DxHDCP_Tst/DxHDCP_Provisioning_Tst/DxHdcp_Provisioning_Tst.c
    - Execute ./DxProvTst on the device
-  Provisioning should be complete successfully, and /persist/data/dxhdcp2/ or /persist/data/sfs/ 
   directory should be created and filled in with data
-  Note: Tool source code under: /master/HDCP/DxHDCP_Tst/DxHDCP_Provisioning_Tst
    - Use the QA_TEST_APP(BBox):
      - When running the test, use [1] - [Provisioning Settings] to provision the device as Transmitter
      - When running the test, use [8] - [Settings] to provision the device as Receiver



<span id="line-101" class="anchor"></span>
**![{\*}](/moin_static194/modernized/img/star_on.png "{*}"){width="16"
height="16"}** **<span class="u">QA Tests</span>** <span id="line-102"
class="anchor"></span><span id="line-103" class="anchor"></span>

#### Linux {#Linux}

<span id="line-104" class="anchor"></span>
**Step 0:** Prepare the QA\_TESTS project environment <span
id="line-105" class="anchor"></span><span id="line-106"
class="anchor"></span>

<span id="line-107" class="anchor"></span><span id="line-108"
class="anchor"></span><span id="line-109" class="anchor"></span><span
id="line-110" class="anchor"></span><span id="line-111"
class="anchor"></span><span id="line-112" class="anchor"></span><span
id="line-113" class="anchor"></span><span id="line-114"
class="anchor"></span><span id="line-115" class="anchor"></span><span
id="line-116" class="anchor"></span><span id="line-117"
class="anchor"></span><span id="line-118" class="anchor"></span><span
id="line-119" class="anchor"></span><span id="line-120"
class="anchor"></span>

    - Modify $(QA_TESTS)/Workspace/ConfigFile.cfg:
      - Modify PLATFORM according to your needs [e.g. PLATFORM=QC2_0_NoSecbuf. This also determines you secure_buf is enabled or disabled]
      - Modify ARM4ROOT to match your environment [e.g. ARM4ROOT=/home/dannys/ARM]
      - Modify ARM5ROOT to match your environment [e.g. ARM5ROOT=/home/dannys/ARM_Compiler_5]
      - Modify NDK_FULL_PATH_LOCATION to match your environment [e.g. NDK_FULL_PATH_LOCATION=/home/dannys/AndroidNDK/android-ndk-r9c]
      - Modify ADB_FULL_PATH_LOCATION [e.g. ADB_FULL_PATH_LOCATION=/usr/bin]
      - Modify TARGET_PLATFORM_TYPE according to your platform and needs [e.g. TARGET_PLATFORM_TYPE=32bit]
      - Modify HDCP_PKG_PATH to the path of the inner HDCP package in your environment [e.g. HDCP_PKG_PATH=../../HDCP/DxHDCP]
      - Modify HDCP_WB_LIB to the path of the libDxHdcpWB.so [e.g HDCP_WB_LIB=../../HDCP/DxHDCPPackage/WB_TESTS/hlos/Release/32bit/libDxHdcpWB.so]
      - Modify TZ_PLATFORMS_ROOT to match your environment [e.g. TZ_PLATFORMS_ROOT=/shared/data/winshare/Proj/TZPlatforms_Trunk_MainProject]

    - Modify $(QA_TESTS)/Workspace/cfg_files/<Platform_Specific_Config_File>:
      - Modify TZ_TRUSTLET_BUILD_FLAGS according to your device characteristics [e.g. export TZ_TRUSTLET_BUILD_FLAGS="-p Mediatek -m mt6752 -v L0.MP6.p11"]

<span id="line-121" class="anchor"></span>
**Step 1:** Build the QA\_TESTS project, and push files into the device
<span id="line-122" class="anchor"></span><span id="line-123"
class="anchor"></span>

For building **BB Internal tests** and **WB tests**: <span id="line-124"
class="anchor"></span><span id="line-125" class="anchor"></span>

<span id="line-126" class="anchor"></span><span id="line-127"
class="anchor"></span>

    From $(QA_TESTS)/Scripts, run ./BuildQA_Package.sh

<span id="line-128" class="anchor"></span>
For building **BB External tests**: <span id="line-129"
class="anchor"></span><span id="line-130" class="anchor"></span>

<span id="line-131" class="anchor"></span><span id="line-132"
class="anchor"></span>

    - From $(QA_TESTS)/.., run ./ExtCompile.sh

<span id="line-133" class="anchor"></span><span id="line-134"
class="anchor"></span>
For pushing all **tests executable files** and **tests data files** into
your device: <span id="line-135" class="anchor"></span><span
id="line-136" class="anchor"></span><span id="line-137"
class="anchor"></span><span id="line-138" class="anchor"></span><span
id="line-139" class="anchor"></span>

    From $(QA_TESTS)/.., run:
    - ./ExtPushFiles.sh 'adb -s <device_adb_id>'
    - ./IntPushFiles.sh 'adb -s <device_adb_id>'

<span id="line-140" class="anchor"></span><span id="line-141"
class="anchor"></span>
In case **secure\_buf is enabled**, push the QA trustlets to the device:
<span id="line-142" class="anchor"></span><span id="line-143"
class="anchor"></span><span id="line-144" class="anchor"></span><span
id="line-145" class="anchor"></span><span id="line-146"
class="anchor"></span><span id="line-147" class="anchor"></span><span
id="line-148" class="anchor"></span><span id="line-149"
class="anchor"></span><span id="line-150" class="anchor"></span>

    Note: The commands below refer to Mediatek. For other platforms, change accordingly,

    - From $(QA_TESTS)/QA_Trustlet/Service/workspace/obj/Mediatek/Tests_QATrustlet-release-Mediatek/GNU/intermediate-QATrustlet, run: 
    adb push ffffffff000000000000000000000017.tlbin /system/app/mcRegistry

    - From $(QA_TESTS)/QA_Trustlet/IService/workspace/obj/Mediatek/Tests_IQTrustlet-release-Mediatek/GNU/intermediate-IQTrustlet, run: 
    adb push ffffffff000000000000000000000018.tlbin /system/app/mcRegistry

<span id="line-151" class="anchor"></span>
**Step 2:** Push all **HDCP** files (\*.so, \*.cfg, TZ files) to the
devices <span id="line-152" class="anchor"></span><span id="line-153"
class="anchor"></span>

<span id="line-154" class="anchor"></span><span id="line-155"
class="anchor"></span><span id="line-156" class="anchor"></span><span
id="line-157" class="anchor"></span>

    #adb push libs/armeabi/libDxHdcp.so /system/lib/libDxHdcp.so
    #adb push external/HDCP_API/DxHDCP.cfg /system/etc
    Use Push.sh to push TZ files

<span id="line-158" class="anchor"></span>
**Step 3:** Modify wifi PS settings on the devices <span id="line-159"
class="anchor"></span><span id="line-160" class="anchor"></span>

<span id="line-161" class="anchor"></span><span id="line-162"
class="anchor"></span><span id="line-163" class="anchor"></span><span
id="line-164" class="anchor"></span><span id="line-165"
class="anchor"></span>

    Set values in /data/misc/wifi/WCNSS_qcom_cfg.ini [sometimes in /etc/wifi/WCNSS_qcom_cfg.ini] as follows (to achieve 7ms ping):
    gEnableBmps=0
    gEnableImps=0
    gDot11Mode=3

<span id="line-166" class="anchor"></span>
**Step 4:** Run the tests <span id="line-167"
class="anchor"></span><span id="line-168" class="anchor"></span>

<span id="line-169" class="anchor"></span><span id="line-170"
class="anchor"></span><span id="line-171" class="anchor"></span><span
id="line-172" class="anchor"></span><span id="line-173"
class="anchor"></span><span id="line-174" class="anchor"></span><span
id="line-175" class="anchor"></span>

    - Connect 2 devices using wifi (softAp & wifi STA)
    - Make sure ping is less than 7ms (See Step 3)
    - Receiver BB: From /data/tmp/Receivers/RCV1/RCV, run ./DX_QA_HDCP_Sink -t <sink_IP>:1900
    - Transmitter BB: From /data/tmp/Transmitter, run ./DX_QA_HDCP_Transmitter -t <sink_IP>:1900 [Use ./IDX_QA_HDCP_Transmitter for Internal tests]
    - Receiver WB: From /data/tmp/Receivers/RCV1/RCV, run ./DX_WB_QA_HDCP_Sink -t <sink_IP>:1900
    - Transmitter WB: From /data/tmp/Transmitter, run ./DX_WB_QA_HDCP_Transmitter -t <sink_IP>:1900

<span id="line-176" class="anchor"></span>

#### Windows {#Windows}

<span id="line-177" class="anchor"></span>
-   No need in devices for Win tests <span id="line-178"
    class="anchor"></span>
-   Name your **HDCP**\_PROJ directory "SUT", and have it in parallel to
    \$QA\_Dx**HDCP**\_TST <span id="line-179" class="anchor"></span>
-   Load [Dx**Hdcp**](/DxHdcp){.nonexistent}.sln under
    \$**HDCP**\_PROJ\\[WorkSpace](/WorkSpace){.nonexistent}\\Win and
    build it <span id="line-180" class="anchor"></span>
-   Load QA\_WB\_Dx**HDCP**\_TST.sln \[or QA\_Dx**HDCP**\_TST.sln\]
    under \$QA\_Dx**HDCP**\_TST\\Workspace and build it <span
    id="line-181" class="anchor"></span>
-   Right click on QA\_DxDH**CP**\_Sink project: debug-&gt;start new
    instance <span id="line-182" class="anchor"></span>
-   Right click on QA\_DxDH**CP**\_Transmitter project: debug-&gt;start
    new instance <span id="line-183" class="anchor"></span><span
    id="line-184" class="anchor"></span>

<span class="u">Note</span>: You need to have config files under c:\\tmp
as described below <span id="line-185" class="anchor"></span><span
id="line-186" class="anchor"></span>

-   Copy Dx**HDCP**.cfg from the **HDCP** project to c:\\tmp and
    generate copies of this file in the following names:
    Dx\_Tsmt\_**HDCP**.cfg, Dx**HDCP**Tsmt.cfg, Dx\_Rcv\_**HDCP**.cfg,
    Dx\_Rpt\_**HDCP**.cfg <span id="line-187" class="anchor"></span>
    -   Dx\_Tsmt\_**HDCP**.cfg, Dx**HDCP**Tsmt.cfg - Identical files
        with "[LogFile](/LogFile){.nonexistent}=**HDCP**\_TSMT" inside
        <span id="line-188" class="anchor"></span>
    -   Dx**HDCP**.cfg, Dx\_Rcv\_**HDCP**.cfg, Dx\_Rpt\_**HDCP**.cfg -
        Identical files with
        "[LogFile](/LogFile){.nonexistent}=**HDCP**\_RCV" inside <span
        id="line-189" class="anchor"></span>
-   Make sure the cfg files under QA\_Dx**HDCP**\_TST\\Workspace contain
    your PC IP address, and all contain the same RMI port number <span
    id="line-190" class="anchor"></span>
-   You can use these config files for example \[don't forget to change
    the IP address to match your PC IP) -
    [WinCfgFiles.zip](/CP/PRODUCTS/HA/KB/HDCP_Ref_Guide?action=AttachFile&do=view&target=WinCfgFiles.zip){.attachment}
    <span id="line-191" class="anchor"></span><span id="line-192"
    class="anchor"></span>

**![{\*}](/moin_static194/modernized/img/star_on.png "{*}"){width="16"
height="16"}** **<span class="u">Debug</span>** <span id="line-193"
class="anchor"></span><span id="line-194" class="anchor"></span>

#### HLOS {#HLOS-1}

<span id="line-195" class="anchor"></span>
<span id="line-196" class="anchor"></span><span id="line-197"
class="anchor"></span><span id="line-198" class="anchor"></span><span
id="line-199" class="anchor"></span><span id="line-200"
class="anchor"></span><span id="line-201" class="anchor"></span><span
id="line-202" class="anchor"></span><span id="line-203"
class="anchor"></span>

    In config file [DxHDCP.cfg]:
    EnableLogs=True [Must be true to get ANY logs in HLOS]
    LogcatLogs=True [If True, most HLOS printouts will go into logcat. Better to use this because otherwise writing to the *.DxLog file slows the system]

    * Viewing DxModule printouts: adb -s c0b528c1 logcat -v threadtime | grep DxModule

    * Viewing Qualcomm's printouts: adb -s c0b528c1 logcat -v threadtime | grep QSEE

<span id="line-204" class="anchor"></span>

#### TZ {#TZ-1}

<span id="line-205" class="anchor"></span>
<span id="line-206" class="anchor"></span><span id="line-207"
class="anchor"></span><span id="line-208" class="anchor"></span><span
id="line-209" class="anchor"></span>

    Using the debug version is nearly impossible due to system slowness. That's why:
    DxHwLogTrace - These printouts are seen only on debug version
    DxHwLogError - These printouts are seen on both release & debug versions

<span id="line-210" class="anchor"></span>

#### More debug tips {#More_debug_tips}

<span id="line-211" class="anchor"></span>
<span id="line-212" class="anchor"></span><span id="line-213"
class="anchor"></span><span id="line-214" class="anchor"></span><span
id="line-215" class="anchor"></span>

    * Viewing entry point address:
    adb -s c0b528c1 pull /firmware/image/dxhdcp2.mdt
    readelf -h dxhdcp2.mdt [expected entry point address: 0x88e00000]

<span id="line-216" class="anchor"></span>
**![{\*}](/moin_static194/modernized/img/star_on.png "{*}"){width="16"
height="16"}** **<span class="u">Useful Tools</span>** <span
id="line-217" class="anchor"></span><span id="line-218"
class="anchor"></span>

<span class="u">t**cp**dump</span> <span id="line-219"
class="anchor"></span>

-   If not exist on your device, put attached t**cp**dump file
    ([t**cp**dump](/CP/PRODUCTS/HA/KB/HDCP_Ref_Guide?action=AttachFile&do=view&target=tcpdump){.attachment})
    on the device (usually in /system/xbin) <span id="line-220"
    class="anchor"></span>
-   To run t**cp**dump, use the command: *./t**cp**dump -i any -p -s 0
    -w capture.pcap* <span id="line-221" class="anchor"></span><span
    id="line-222" class="anchor"></span>

**![{\*}](/moin_static194/modernized/img/star_on.png "{*}"){width="16"
height="16"}** **<span class="u">Using a dongle</span>** <span
id="line-223" class="anchor"></span><span id="line-224"
class="anchor"></span>

-   Build a dongle setup according to the attached image -
    [DongleSetup.jpg](/CP/PRODUCTS/HA/KB/HDCP_Ref_Guide?action=AttachFile&do=view&target=DongleSetup.jpg){.attachment}
    <span id="line-225" class="anchor"></span>
-   On the device, make sure that: <span id="line-226"
    class="anchor"></span>
    -   The file: */system/lib/libwfd**hdcpcp**.so* exists. <span
        id="line-227" class="anchor"></span>
    -   */system/etc/wfdconfig.xml* contains a tag inside
        **Capabilities** that is called
        **[ContentProtection](/ContentProtection){.nonexistent}**. It
        has a parameter called **Valid** (on some platforms it is called
        *****HDCP**Valid***). It should be set to 1. <span id="line-228"
        class="anchor"></span>
-   From your device, run the **Wfd client** application <span
    id="line-229" class="anchor"></span>
-   Press the **search peers** button, and connect to the dongle found
    in the peers' list <span id="line-230" class="anchor"></span>
-   After connection is established, press the **start session** button
    that should appear <span id="line-231" class="anchor"></span><span
    id="line-232" class="anchor"></span>

==&gt; The monitor should show the same "screen" showed on your device
<span id="line-233" class="anchor"></span><span id="line-234"
class="anchor"></span>

-   Last step is to make sure that Dx **HDCP** is used for
    authentication and encryption - For this purpose use logcat (See
    **Debug** section on this page) <span id="line-235"
    class="anchor"></span><span id="line-236" class="anchor"></span>

**![{\*}](/moin_static194/modernized/img/star_on.png "{*}"){width="16"
height="16"}** **<span class="u">Links</span>** <span id="line-237"
class="anchor"></span><span id="line-238" class="anchor"></span>

[**HDCP** **Products** Page](/CP/PRODUCTS/HDCP) <span id="line-239"
class="anchor"></span><span id="line-240" class="anchor"></span>

[Using a Dongle](/CP/PRODUCTS/HDCP/DONGLES) <span id="line-241"
class="anchor"></span><span id="line-242" class="anchor"></span>

[Flashing a Dongle](/CP/PS/DEVICES/Flash_LG_HDCP_Dongle) <span
id="line-243" class="anchor"></span><span id="line-244"
class="anchor"></span>

[Using Minicom](/CP/PS/DEVICES/Using_Minicom) <span id="line-245"
class="anchor"></span><span id="line-246" class="anchor"></span>

[New BuildBot Wiki](http://dxcpbuildbot:6060){.http} <span id="line-247"
class="anchor"></span><span id="bottom" class="anchor"></span>

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
