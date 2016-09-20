<div id="header">

<div>

Search:

</div>

<div id="logo">

[![MoinMoin Logo](/moin_static194/common/moinmoin.png)](/FrontPage)

</div>

<span id="pagelocation"><span class="pagepath">[CP](/CP)<span class="sep">/</span>[PRODUCTS](/CP/PRODUCTS)<span class="sep">/</span>[HA](/CP/PRODUCTS/HA)<span class="sep">/</span>[KB](/CP/PRODUCTS/HA/KB){.nonexistent}</span><span class="sep">/</span>[HDCP\_WinTH\_Guide](/CP/PRODUCTS/HA/KB/HDCP_WinTH_Guide?action=fullsearch&value=linkto%3A%22CP%2FPRODUCTS%2FHA%2FKB%2FHDCP_WinTH_Guide%22&context=180 "Click to do a full-text search for this title"){.backlink}</span> {#locationline}
===================================================================================================================================================================================================================================================================================================================================================================================================================================================================================

-   [RecentChanges](/RecentChanges)
-   [FindPage](/FindPage)
-   [HelpContents](/HelpContents)
-   [HDCP\_WinTH\_Guide](/CP/PRODUCTS/HA/KB/HDCP_WinTH_Guide)

<div id="pageline">

------------------------------------------------------------------------

</div>

</div>

<div id="page" lang="en" dir="ltr">

<div id="content" dir="ltr" lang="en">

<span id="top" class="anchor"></span> <span id="line-1"
class="anchor"></span>

<div class="table-of-contents">

Contents

1.  [HDCP on Windows Threshold
    (Windows 10)](#HDCP_on_Windows_Threshold_.28Windows_10.29)
    1.  [Development Environment
        Prerequisite](#Development_Environment_Prerequisite)
    2.  [Supported platforms](#Supported_platforms)
    3.  [Building the project](#Building_the_project)
        1.  [Git information](#Git_information)
        2.  [Environment](#Environment)
        3.  [Build steps](#Build_steps)

    4.  [Test setup deployment](#Test_setup_deployment)
    5.  [Provisioning](#Provisioning)
        1.  [Using QC Tool](#Using_QC_Tool)
        2.  [Using the Internal Utility](#Using_the_Internal_Utility)

    6.  [Running internal tests](#Running_internal_tests)
        1.  [SW Receiver set-up](#SW_Receiver_set-up)
        2.  [Device transmitter set-up](#Device_transmitter_set-up)

    7.  [Running End-2-End tests](#Running_End-2-End_tests)
    8.  [HDCP Logging](#HDCP_Logging)
    9.  [Packaging](#Packaging)

</div>

<span id="line-2" class="anchor"></span><span id="line-3"
class="anchor"></span>

HDCP on Windows Threshold (Windows 10) {#HDCP_on_Windows_Threshold_.28Windows_10.29}
======================================

<span id="line-4" class="anchor"></span>
This page describes how to build a testing setup for HDCP on Windows 10
platforms. <span id="line-5" class="anchor"></span><span id="line-6"
class="anchor"></span>

Development Environment Prerequisite {#Development_Environment_Prerequisite}
------------------------------------

<span id="line-7" class="anchor"></span>
For Windows 10 Development Environment see **Development Environment
Check List** and **Windows 10 Toolchain Setup** parts in [Windows
Threshold
Page](https://github.com/ARMmbed/ta-TZInfra/blob/master/docs/windows-threshold/README.md){.https}.
<span id="line-8" class="anchor"></span><span id="line-9"
class="anchor"></span>

Supported platforms {#Supported_platforms}
-------------------

<span id="line-10" class="anchor"></span>
-   Qualcomm's msm8994 <span id="line-11" class="anchor"></span>
-   Qualcomm's msm8996 <span id="line-12" class="anchor"></span><span
    id="line-13" class="anchor"></span>

Building the project {#Building_the_project}
--------------------

<span id="line-14" class="anchor"></span>

### Git information {#Git_information}

<span id="line-15" class="anchor"></span>
-   **DxHDCP\_for\_Windows\_Threshold** branch from the
    *<git@github.com> :ARMmbed/ta-DxHDCP.git* repository <span
    id="line-16" class="anchor"></span><span id="line-17"
    class="anchor"></span>

### Environment {#Environment}

<span id="line-18" class="anchor"></span>
The project is built using Visual Studio 2013 for msm8994 platform and
Visual Studio 2015 for msm8996 platform <span id="line-19"
class="anchor"></span><span id="line-20" class="anchor"></span>

\* Clone the HDCP repository from [GitHub](/GitHub){.nonexistent} to
your **&lt;HDCP\_ROOT&gt;** directory and checkout the
**DxHDCP\_for\_Windows\_Threshold** branch. <span id="line-21"
class="anchor"></span><span id="line-22" class="anchor"></span>

\* Generate the HDCP project files <span id="line-23"
class="anchor"></span><span id="line-24" class="anchor"></span>

1.  Open cmd <span id="line-25" class="anchor"></span>
2.  cd to &lt;HDCP\_ROOT&gt; <span id="line-26" class="anchor"></span>
3.  To generate project files run: <span id="line-27"
    class="anchor"></span>

    <span class="u">msm8994 (Visual Studio 2013)</span>: <span
    id="line-28" class="anchor"></span><span id="line-29"
    class="anchor"></span><span id="line-30" class="anchor"></span><span
    id="line-31" class="anchor"></span>

             python project_builder.py -p WoS_ARM_VS2013 config generate --TZ_PLATFORMS_ROOT=<Location of TZPlatforms> --PLAT_QC_WOS_GIT_REPO_TEMPLATE={qc_platform}_amss_device
                                       --PLAT_QUALCOMM_WA_PLATFORM=msm8994-wp-1-0 --PLAT_QUALCOMM_WA_QC_RELEASE=1073.1 --TZ_VERSION=3.0

    <span id="line-32" class="anchor"></span>

    <span class="u">msm8996 (Visual Studio 2015)</span>: <span
    id="line-33" class="anchor"></span><span id="line-34"
    class="anchor"></span><span id="line-35" class="anchor"></span><span
    id="line-36" class="anchor"></span>

             python project_builder.py -p WoS_ARM_VS2015 config generate --TZ_PLATFORMS_ROOT=<Location of TZPlatforms> --PLAT_QC_WOS_GIT_REPO_TEMPLATE={qc_platform}_tzap_dev
                                       --PLAT_QUALCOMM_WA_PLATFORM=msm8996-wp-1-0 --PLAT_QUALCOMM_WA_QC_RELEASE=01700.1a --TZ_VERSION=4.0

    <span id="line-37" class="anchor"></span><span id="line-38"
    class="anchor"></span><span id="line-39" class="anchor"></span><span
    id="line-40" class="anchor"></span><span id="line-41"
    class="anchor"></span>

    <div class="important">

    <span id="line-1-1" class="anchor"></span>
    -   The current msm8996 device HW available (DXSN 2573) forces us to
        build with QC build release 01700.1a <span id="line-2-1"
        class="anchor"></span>
    -   If building for a different HW, need to check which QC build
        release should be used and set the
        **PLAT\_QUALCOMM\_WA\_QC\_RELEASE** flag accordingally. <span
        id="line-3-1" class="anchor"></span>

        -   For example: *--PLAT\_QUALCOMM\_WA\_QC\_RELEASE=42000.1*

    </div>

    <span id="line-42" class="anchor"></span>

4.  You now have an updated Visual Studio solution
    file (DxHDCP\_vs&lt;2013/2015&gt;.sln) under
    &lt;HDCP\_ROOT&gt;\\<span
    class="u">\_build\_vs&lt;2013/2015&gt;</span> and a shortcut to it
    under &lt;HDCP\_ROOT&gt;. <span id="line-43"
    class="anchor"></span><span id="line-44" class="anchor"></span>

### Build steps {#Build_steps}

<span id="line-45" class="anchor"></span>
-   Open Visual Studio (2013/2015) <span id="line-46"
    class="anchor"></span>
-   In the **Solution Configurations** dropdown choose
    **Release\_dynamic** or **Debug\_dynamic**. <span id="line-47"
    class="anchor"></span>
-   Build the solution, it will build both HLOS and TZ binaries
    (including the postbuild phase) as well as the test executables.
    <span id="line-48" class="anchor"></span>
-   Build products information (For Release\_dynamic solution
    configuration, TZ compiled with test keys): <span id="line-49"
    class="anchor"></span>
    <div>

    **msm8994 (Visual Studio 2013)**
    **msm8996 (Visual Studio 2015)**
    <span id="line-50" class="anchor"></span>
    **HLOS products Location**
    \\<span
    class="u">\_build\_vs2013</span>\\WoS\_ARM-120-Release\_dynamic
    \\<span
    class="u">\_build\_vs2015</span>\\WoS\_ARM-140-Release\_dynamic
    <span id="line-51" class="anchor"></span>
    **HDCP HLOS library**
    [DxHdcp](/DxHdcp){.nonexistent}\_WP10\_vc120\_Mt.dll
    [DxHdcp](/DxHdcp){.nonexistent}\_WP10\_vc140\_Mt.dll
    <span id="line-52" class="anchor"></span>
    **Test executables**
    QA\_DxHDCP\_Transmitter\_WoS.exe, IQA\_DxHDCP\_Transmitter\_WoS.exe
    <span id="line-53" class="anchor"></span>
    **Internal Provisioning utility**
    [ProvApp](/ProvApp){.nonexistent}\_WoS.exe
    <span id="line-54" class="anchor"></span>
    **TZ products Location**
    &lt;HDCP\_ROOT&gt;\\<span class="u">\_build </span>
    <span id="line-55" class="anchor"></span>
    **TZ HDCP library (postbuild input)**
    dxhdcp2-release-Tst.lib
    <span id="line-56" class="anchor"></span>
    **TZ HDCP app (postbuild output)**
    dxhdcp2-release-Tst-msm8994-wp-1-0-1073.1.mbn
    dxhdcp2-release-Tst-msm8996-wp-1-0-01700.1a.mbn

    </div>

    <span id="line-57" class="anchor"></span><span id="line-58"
    class="anchor"></span><span id="line-59" class="anchor"></span><span
    id="line-60" class="anchor"></span>

<span id="line-61" class="anchor"></span><span id="line-62"
class="anchor"></span><span id="line-63" class="anchor"></span><span
id="line-64" class="anchor"></span><span id="line-65"
class="anchor"></span><span id="line-66" class="anchor"></span>

<div class="important">

<span id="line-1-2" class="anchor"></span>
-   If you wish to skip the postbuild phase add
    **--TRUSTZONE\_SKIP\_POSTBUILD=True** to the project generation
    command (project\_builder.py), the TZ build will now stop after
    creating the .lib file. <span id="line-2-2" class="anchor"></span>
-   The postbuild phase clones the relevant QC source tree and checkouts
    the relevant tag. <span id="line-3-2" class="anchor"></span>
    -   If you already cloned the QC source tree to the appropriate
        **DX\_PREFIX\_PATH** it will only try to update with the server
        using *git fetch*. <span id="line-4-1" class="anchor"></span>
    -   You can skip this update step by giving
        *--PLAT\_QC\_WOS\_GIT\_SKIP\_UPDATE=true*
        to project\_builder.py. (Very helpful when working without
        internet connection). <span id="line-5-1" class="anchor"></span>
-   There are more parameters which can be given to this script, you can
    see them by running: *python project\_builder.py -p WoS\_ARM\_VS2015
    -h*

</div>

<span id="line-67" class="anchor"></span>

Test setup deployment {#Test_setup_deployment}
---------------------

<span id="line-68" class="anchor"></span>
1.  Connect to the device using Power shell as described in the
    **Connect to Windows phone device** part in [Windows Threshold
    Page](https://github.com/ARMmbed/ta-TZInfra/blob/master/docs/windows-threshold/README.md){.https}.
    <span id="line-69" class="anchor"></span><span id="line-70"
    class="anchor"></span>
2.  Change remote directory to *c:\\data\\test\\bin*. <span id="line-71"
    class="anchor"></span><span id="line-72" class="anchor"></span>
3.  Push HLOS build products to the device by running the following
    commands: <span id="line-73" class="anchor"></span><span
    id="line-74" class="anchor"></span><span id="line-75"
    class="anchor"></span><span id="line-76" class="anchor"></span><span
    id="line-77" class="anchor"></span><span id="line-78"
    class="anchor"></span>

        putd DxHdcp_WP10_vc140_Mt.dll .
        putd IQA_DxHDCP_Transmitter_WoS.exe .
        putd QA_DxHDCP_Transmitter_WoS.exe .
        putd ProvApp_WoS.exe .

    <span id="line-79" class="anchor"></span>The expected output should
    be as follows: <span id="line-80" class="anchor"></span><span
    id="line-81" class="anchor"></span><span id="line-82"
    class="anchor"></span><span id="line-83" class="anchor"></span><span
    id="line-84" class="anchor"></span><span id="line-85"
    class="anchor"></span><span id="line-86" class="anchor"></span><span
    id="line-87" class="anchor"></span><span id="line-88"
    class="anchor"></span><span id="line-89" class="anchor"></span><span
    id="line-90" class="anchor"></span><span id="line-91"
    class="anchor"></span><span id="line-92" class="anchor"></span><span
    id="line-93" class="anchor"></span><span id="line-94"
    class="anchor"></span><span id="line-95" class="anchor"></span><span
    id="line-96" class="anchor"></span><span id="line-97"
    class="anchor"></span>

         DEVICE c:\data\test\bin
         PS C:\Projects\DxHDCP_for_Windows_Threshold\__build_vs2015\WoS_ARM-140-Release_dynamic> putd DxHdcp_WP10_vc140_Mt.dll .
         C:\Projects\DxHDCP_for_Windows_Threshold\__build_vs2015\WoS_ARM-140-Release_dynamic\DxHdcp_WP10_vc140_Mt.dll
         1 file(s) copied to device.
         DEVICE c:\data\test\bin
         PS C:\Projects\DxHDCP_for_Windows_Threshold\__build_vs2015\WoS_ARM-140-Release_dynamic> putd IQA_DxHDCP_Transmitter_WoS.exe .
         C:\Projects\DxHDCP_for_Windows_Threshold\__build_vs2015\WoS_ARM-140-Release_dynamic\IQA_DxHDCP_Transmitter_WoS.exe
         1 file(s) copied to device.
         DEVICE c:\data\test\bin
         PS C:\Projects\DxHDCP_for_Windows_Threshold\__build_vs2015\WoS_ARM-140-Release_dynamic> putd QA_DxHDCP_Transmitter_WoS.exe .
         C:\Projects\DxHDCP_for_Windows_Threshold\__build_vs2015\WoS_ARM-140-Release_dynamic\QA_DxHDCP_Transmitter_WoS.exe
         1 file(s) copied to device.
         DEVICE c:\data\test\bin
         PS C:\Projects\DxHDCP_for_Windows_Threshold\__build_vs2015\WoS_ARM-140-Release_dynamic> putd ProvApp_WoS.exe .
         C:\Projects\DxHDCP_for_Windows_Threshold\__build_vs2015\WoS_ARM-140-Release_dynamic\ProvApp_WoS.exe
         1 file(s) copied to device.

    <span id="line-98" class="anchor"></span>

4.  Push TZ application (.mbn file) to the device by following the steps
    as described in the **Mass Storage mode** part in [Windows Threshold
    Page](https://github.com/ARMmbed/ta-TZInfra/blob/master/docs/windows-threshold/README.md){.https}
    (Example below on msm8994 device already in FFU mode). <span
    id="line-99" class="anchor"></span><span id="line-100"
    class="anchor"></span><span id="line-101"
    class="anchor"></span><span id="line-102"
    class="anchor"></span><span id="line-103"
    class="anchor"></span><span id="line-104"
    class="anchor"></span><span id="line-105"
    class="anchor"></span><span id="line-106"
    class="anchor"></span><span id="line-107"
    class="anchor"></span><span id="line-108"
    class="anchor"></span><span id="line-109"
    class="anchor"></span><span id="line-110"
    class="anchor"></span><span id="line-111"
    class="anchor"></span><span id="line-112"
    class="anchor"></span><span id="line-113"
    class="anchor"></span><span id="line-114"
    class="anchor"></span><span id="line-115"
    class="anchor"></span><span id="line-116"
    class="anchor"></span><span id="line-117"
    class="anchor"></span><span id="line-118"
    class="anchor"></span><span id="line-119"
    class="anchor"></span><span id="line-120"
    class="anchor"></span><span id="line-121"
    class="anchor"></span><span id="line-122"
    class="anchor"></span><span id="line-123"
    class="anchor"></span><span id="line-124"
    class="anchor"></span><span id="line-125"
    class="anchor"></span><span id="line-126"
    class="anchor"></span><span id="line-127"
    class="anchor"></span><span id="line-128"
    class="anchor"></span><span id="line-129"
    class="anchor"></span><span id="line-130"
    class="anchor"></span><span id="line-131" class="anchor"></span>

         Y:\CP\HWA\WindowsThreshold\Qualcomm\Burn_and_config_Tools>ffutool -massStorage
         Success, device resetting to mass storage mode.

         Y:\CP\HWA\WindowsThreshold\Qualcomm\Burn_and_config_Tools>"tzapps partition\find_tzapps_partition.bat"
         Found TZAPPS in \\?\harddisk1partition24\\tzapps\

         REM Copy the .mbn file as dxhdcp2.mbn to the folder found in previous step.
         Y:\CP\HWA\WindowsThreshold\Qualcomm\Burn_and_config_Tools>copy "C:\tmp\__build\dxhdcp2-release-Tst-msm8994-wp-1-0-1073.1.mbn" \\?\harddisk1partition24\\tzapps\dxhdcp2.mbn
               1 file(s) copied.

         Y:\CP\HWA\WindowsThreshold\Qualcomm\Burn_and_config_Tools>dir \\?\harddisk1partition24\\tzapps
          Volume in drive \\?\harddisk1partition24 has no label.
          Volume Serial Number is 3046-D4D7

          Directory of \\?\harddisk1partition24\tzapps

         07/07/2011  02:07 PM    <DIR>          .
         07/07/2011  02:07 PM    <DIR>          ..
         09/17/2015  02:06 PM           107,020 uefi_sec.mbn
         09/17/2015  08:17 AM           189,884 issw_ape.mbn
         09/17/2015  02:06 PM           143,688 cmnlib.mbn
         09/17/2015  02:06 PM           260,676 pr_3_0.mbn
         09/17/2015  08:17 AM           189,884 issw0.mbn
         09/17/2015  08:17 AM           189,884 issw1.mbn
         09/17/2015  08:17 AM           189,884 issw2.mbn
         09/17/2015  08:17 AM           189,884 issw3.mbn
         09/17/2015  08:17 AM           189,884 issw4.mbn
         09/17/2015  08:17 AM           189,888 isswraml.mbn
         04/07/2016  09:25 AM           188,748 dxhdcp2.mbn
                      11 File(s)      2,029,324 bytes
                       2 Dir(s)      14,598,144 bytes free

    <span id="line-132" class="anchor"></span>

5.  Push Transmitter's configuration file to the device as
    *Dx\_Tsmt\_HDCP.cfg* <span id="line-133" class="anchor"></span><span
    id="line-134" class="anchor"></span><span id="line-135"
    class="anchor"></span><span id="line-136"
    class="anchor"></span><span id="line-137"
    class="anchor"></span><span id="line-138" class="anchor"></span>

         DEVICE c:\data\test\bin
         PS C:\Projects\DxHDCP_for_Windows_Threshold\__build_vs2015\WoS_ARM-140-Release_dynamic> putd ..\..\HDCP\external\HDCP_API\DxHDCP_WoS.cfg Dx_Tsmt_HDCP.cfg
         C:\Projects\DxHDCP_for_Windows_Threshold\HDCP\external\HDCP_API\DxHDCP_WoS.cfg
         1 file(s) copied to device.

    <span id="line-139" class="anchor"></span>

6.  Push *HDCP2\_Cek.dat* and *HDCP2\_Tsmt\_Tst.dat* from
    **&lt;HDCP\_ROOT&gt;\\QA\_DxHDCP\_TST\\[ProvisioningFolder](/ProvisioningFolder){.nonexistent}**
    to device, these files are input for the internal Provisioning
    utility (*[ProvApp](/ProvApp){.nonexistent}\_WoS.exe*) <span
    id="line-140" class="anchor"></span><span id="line-141"
    class="anchor"></span><span id="line-142"
    class="anchor"></span><span id="line-143"
    class="anchor"></span><span id="line-144"
    class="anchor"></span><span id="line-145"
    class="anchor"></span><span id="line-146"
    class="anchor"></span><span id="line-147"
    class="anchor"></span><span id="line-148"
    class="anchor"></span><span id="line-149"
    class="anchor"></span><span id="line-150"
    class="anchor"></span><span id="line-151" class="anchor"></span>

         DEVICE c:\data\test\bin
         PS C:\Projects\DxHDCP_for_Windows_Threshold\__build_vs2015\WoS_ARM-140-Release_dynamic> cd C:\Projects\DxHDCP_for_Windows_Threshold\QA_DxHDCP_TST\ProvisioningFolder
         DEVICE c:\data\test\bin
         PS C:\Projects\DxHDCP_for_Windows_Threshold\QA_DxHDCP_TST\ProvisioningFolder> putd HDCP2_Cek.dat .
         C:\Projects\DxHDCP_for_Windows_Threshold\QA_DxHDCP_TST\ProvisioningFolder\HDCP2_Cek.dat
         1 file(s) copied to device.
         DEVICE c:\data\test\bin
         PS C:\Projects\DxHDCP_for_Windows_Threshold\QA_DxHDCP_TST\ProvisioningFolder> putd HDCP2_Tsmt_Tst.dat .
         C:\Projects\DxHDCP_for_Windows_Threshold\QA_DxHDCP_TST\ProvisioningFolder\HDCP2_Tsmt_Tst.dat
         1 file(s) copied to device.

    <span id="line-152" class="anchor"></span>

7.  Push **Test\_Data** and
    **[ProvisioningFolder](/ProvisioningFolder){.nonexistent}**
    directories from **&lt;HDCP\_ROOT&gt;\\QA\_DxHDCP\_TST** to the
    device at c:\\data <span id="line-153" class="anchor"></span><span
    id="line-154" class="anchor"></span><span id="line-155"
    class="anchor"></span><span id="line-156"
    class="anchor"></span><span id="line-157"
    class="anchor"></span><span id="line-158"
    class="anchor"></span><span id="line-159"
    class="anchor"></span><span id="line-160"
    class="anchor"></span><span id="line-161"
    class="anchor"></span><span id="line-162"
    class="anchor"></span><span id="line-163"
    class="anchor"></span><span id="line-164"
    class="anchor"></span><span id="line-165"
    class="anchor"></span><span id="line-166"
    class="anchor"></span><span id="line-167"
    class="anchor"></span><span id="line-168"
    class="anchor"></span><span id="line-169"
    class="anchor"></span><span id="line-170"
    class="anchor"></span><span id="line-171"
    class="anchor"></span><span id="line-172"
    class="anchor"></span><span id="line-173"
    class="anchor"></span><span id="line-174"
    class="anchor"></span><span id="line-175"
    class="anchor"></span><span id="line-176"
    class="anchor"></span><span id="line-177"
    class="anchor"></span><span id="line-178"
    class="anchor"></span><span id="line-179"
    class="anchor"></span><span id="line-180"
    class="anchor"></span><span id="line-181"
    class="anchor"></span><span id="line-182"
    class="anchor"></span><span id="line-183"
    class="anchor"></span><span id="line-184"
    class="anchor"></span><span id="line-185"
    class="anchor"></span><span id="line-186"
    class="anchor"></span><span id="line-187"
    class="anchor"></span><span id="line-188"
    class="anchor"></span><span id="line-189"
    class="anchor"></span><span id="line-190"
    class="anchor"></span><span id="line-191"
    class="anchor"></span><span id="line-192"
    class="anchor"></span><span id="line-193"
    class="anchor"></span><span id="line-194"
    class="anchor"></span><span id="line-195"
    class="anchor"></span><span id="line-196"
    class="anchor"></span><span id="line-197"
    class="anchor"></span><span id="line-198"
    class="anchor"></span><span id="line-199"
    class="anchor"></span><span id="line-200"
    class="anchor"></span><span id="line-201"
    class="anchor"></span><span id="line-202"
    class="anchor"></span><span id="line-203"
    class="anchor"></span><span id="line-204"
    class="anchor"></span><span id="line-205"
    class="anchor"></span><span id="line-206"
    class="anchor"></span><span id="line-207"
    class="anchor"></span><span id="line-208"
    class="anchor"></span><span id="line-209"
    class="anchor"></span><span id="line-210"
    class="anchor"></span><span id="line-211"
    class="anchor"></span><span id="line-212"
    class="anchor"></span><span id="line-213"
    class="anchor"></span><span id="line-214" class="anchor"></span>

         DEVICE c:\data\test\bin
         PS C:\Projects\DxHDCP_for_Windows_Threshold\__build_vs2015\WoS_ARM-140-Release_dynamic> cd C:\Projects\DxHDCP_for_Windows_Threshold\QA_DxHDCP_TST
         DEVICE c:\data\test\bin
         PS C:\Projects\DxHDCP_for_Windows_Threshold\QA_DxHDCP_TST> cdd c:\data
         DEVICE c:\data
         PS C:\Projects\DxHDCP_for_Windows_Threshold\QA_DxHDCP_TST> mkdird Test_Data
         DEVICE c:\data
         PS C:\Projects\DxHDCP_for_Windows_Threshold\QA_DxHDCP_TST> putd Test_Data\* Test_Data
         C:\Projects\DxHDCP_for_Windows_Threshold\QA_DxHDCP_TST\Test_Data\CorruptedSrmID.bin
         C:\Projects\DxHDCP_for_Windows_Threshold\QA_DxHDCP_TST\Test_Data\CorruptedSrmInd.bin
         C:\Projects\DxHDCP_for_Windows_Threshold\QA_DxHDCP_TST\Test_Data\CorruptedSrmSign.bin
         C:\Projects\DxHDCP_for_Windows_Threshold\QA_DxHDCP_TST\Test_Data\CorruptedSrmVersion.bin
         C:\Projects\DxHDCP_for_Windows_Threshold\QA_DxHDCP_TST\Test_Data\HDCP_Test_File1.txt
         C:\Projects\DxHDCP_for_Windows_Threshold\QA_DxHDCP_TST\Test_Data\HDCP_Test_File2.txt
         C:\Projects\DxHDCP_for_Windows_Threshold\QA_DxHDCP_TST\Test_Data\HDCP_Test_File3.txt
         C:\Projects\DxHDCP_for_Windows_Threshold\QA_DxHDCP_TST\Test_Data\HDCP_Test_File4.txt
         C:\Projects\DxHDCP_for_Windows_Threshold\QA_DxHDCP_TST\Test_Data\HDCP_Test_File5.txt
         C:\Projects\DxHDCP_for_Windows_Threshold\QA_DxHDCP_TST\Test_Data\HDCP_Test_File6.txt
         C:\Projects\DxHDCP_for_Windows_Threshold\QA_DxHDCP_TST\Test_Data\HDCP_Test_File7.txt
         C:\Projects\DxHDCP_for_Windows_Threshold\QA_DxHDCP_TST\Test_Data\HDCP_Test_File_Audio.txt
         C:\Projects\DxHDCP_for_Windows_Threshold\QA_DxHDCP_TST\Test_Data\HDCP_Test_File_Video.txt
         C:\Projects\DxHDCP_for_Windows_Threshold\QA_DxHDCP_TST\Test_Data\PCM.bin
         C:\Projects\DxHDCP_for_Windows_Threshold\QA_DxHDCP_TST\Test_Data\test_srm_version_0002.bin
         15 file(s) copied to device.
         DEVICE c:\data
         PS C:\Projects\DxHDCP_for_Windows_Threshold\QA_DxHDCP_TST> mkdird ProvisioningFolder\Receiver-Repeater\HDCP2.1\Set1
         DEVICE c:\data
         PS C:\Projects\DxHDCP_for_Windows_Threshold\QA_DxHDCP_TST> mkdird ProvisioningFolder\Receiver-Repeater\HDCP2.1\Set2
         DEVICE c:\data
         PS C:\Projects\DxHDCP_for_Windows_Threshold\QA_DxHDCP_TST> mkdird ProvisioningFolder\Receiver-Repeater\HDCP2.2\Set1
         DEVICE c:\data
         PS C:\Projects\DxHDCP_for_Windows_Threshold\QA_DxHDCP_TST> mkdird ProvisioningFolder\Receiver-Repeater\HDCP2.2\Set2
         DEVICE c:\data
         PS C:\Projects\DxHDCP_for_Windows_Threshold\QA_DxHDCP_TST> putd ProvisioningFolder\* ProvisioningFolder
         C:\Projects\DxHDCP_for_Windows_Threshold\QA_DxHDCP_TST\ProvisioningFolder\CEK.txt
         C:\Projects\DxHDCP_for_Windows_Threshold\QA_DxHDCP_TST\ProvisioningFolder\HDCP2_Cek.dat
         C:\Projects\DxHDCP_for_Windows_Threshold\QA_DxHDCP_TST\ProvisioningFolder\HDCP2_Cek2.dat
         C:\Projects\DxHDCP_for_Windows_Threshold\QA_DxHDCP_TST\ProvisioningFolder\HDCP2_OemId.dat
         C:\Projects\DxHDCP_for_Windows_Threshold\QA_DxHDCP_TST\ProvisioningFolder\HDCP2_OemId2.dat
         C:\Projects\DxHDCP_for_Windows_Threshold\QA_DxHDCP_TST\ProvisioningFolder\HDCP2_Rcv.dat
         C:\Projects\DxHDCP_for_Windows_Threshold\QA_DxHDCP_TST\ProvisioningFolder\HDCP2_Rcv2.dat
         C:\Projects\DxHDCP_for_Windows_Threshold\QA_DxHDCP_TST\ProvisioningFolder\HDCP2_Tsmt_Tst.dat
         C:\Projects\DxHDCP_for_Windows_Threshold\QA_DxHDCP_TST\ProvisioningFolder\PM.out
         9 file(s) copied to device.
         DEVICE c:\data
         PS C:\Projects\DxHDCP_for_Windows_Threshold\QA_DxHDCP_TST> putd ProvisioningFolder\Receiver-Repeater\HDCP2.1\Set1\* ProvisioningFolder\Receiver-Repeater\HDCP2.1\Set1
         C:\Projects\DxHDCP_for_Windows_Threshold\QA_DxHDCP_TST\ProvisioningFolder\Receiver-Repeater\HDCP2.1\Set1\HDCP2_Rcv.dat
         1 file(s) copied to device.
         DEVICE c:\data
         PS C:\Projects\DxHDCP_for_Windows_Threshold\QA_DxHDCP_TST> putd ProvisioningFolder\Receiver-Repeater\HDCP2.1\Set2\* ProvisioningFolder\Receiver-Repeater\HDCP2.1\Set2
         C:\Projects\DxHDCP_for_Windows_Threshold\QA_DxHDCP_TST\ProvisioningFolder\Receiver-Repeater\HDCP2.1\Set2\HDCP2_Rcv.dat
         1 file(s) copied to device.
         DEVICE c:\data
         PS C:\Projects\DxHDCP_for_Windows_Threshold\QA_DxHDCP_TST> putd ProvisioningFolder\Receiver-Repeater\HDCP2.2\Set1\* ProvisioningFolder\Receiver-Repeater\HDCP2.2\Set1
         C:\Projects\DxHDCP_for_Windows_Threshold\QA_DxHDCP_TST\ProvisioningFolder\Receiver-Repeater\HDCP2.2\Set1\HDCP2_Rcv.dat
         1 file(s) copied to device.
         DEVICE c:\data
         PS C:\Projects\DxHDCP_for_Windows_Threshold\QA_DxHDCP_TST> putd ProvisioningFolder\Receiver-Repeater\HDCP2.2\Set2\* ProvisioningFolder\Receiver-Repeater\HDCP2.2\Set2
         C:\Projects\DxHDCP_for_Windows_Threshold\QA_DxHDCP_TST\ProvisioningFolder\Receiver-Repeater\HDCP2.2\Set2\HDCP2_Rcv.dat
         1 file(s) copied to device.

    <span id="line-215" class="anchor"></span><span id="line-216"
    class="anchor"></span>

Provisioning {#Provisioning}
------------

<span id="line-217" class="anchor"></span>
There are 2 ways to provision a QC
[WindowsPhone](/WindowsPhone){.nonexistent} device, one with a tool
supplied by Qualcomm and the other with an internal utility supplied by
us. <span id="line-218" class="anchor"></span><span id="line-219"
class="anchor"></span>

<span id="line-220" class="anchor"></span><span id="line-221"
class="anchor"></span>

<div class="important">

<span id="line-1-3" class="anchor"></span>
msm8996 devices using QC release 01700.1a must use the internal
provisioning utility due to bugs in the QC tool in the release.

</div>

<span id="line-222" class="anchor"></span>

### Using QC Tool {#Using_QC_Tool}

<span id="line-223" class="anchor"></span>
The official way to provision a QC
[WindowsPhone](/WindowsPhone){.nonexistent} device is to use the QC tool
**QCPhoneProvTool**. <span id="line-224" class="anchor"></span><span
id="line-225" class="anchor"></span>

Here the CEK & data are stored into a special partition (DPP) and at the
UEFI boot stage passed to the HDCP [TrustZone](/TrustZone){.nonexistent}
application. <span id="line-226" class="anchor"></span><span
id="line-227" class="anchor"></span>

This happens on every boot. <span id="line-228"
class="anchor"></span><span id="line-229" class="anchor"></span>

-   Copy *QCPhoneProvTool.exe* from QC's tree to the device at
    *c:\\data\\test\\bin*. <span id="line-230" class="anchor"></span>

    -   Location for 8994:
        **C:\\Git\\msm8994-wp-1-0\_amss\_device\\WP\\prebuilt\\8994\\app\\[FactoryTools](/FactoryTools){.nonexistent}\\QCPhoneProvTool**
        <span id="line-231" class="anchor"></span>
    -   Location for 8996:
        **C:\\Git\\msm8996-wp-1-0\_tzap\_dev\\WP\\prebuilt\\8996\\app\\[FactoryTools](/FactoryTools){.nonexistent}\\QCPhoneProvTool**
        <span id="line-232" class="anchor"></span>
-   Copy *HDCP2\_Cek.dat* and *HDCP2\_Tsmt\_Tst.dat* to the device - See
    part 6 of **Test setup deployment**. <span id="line-233"
    class="anchor"></span>
-   Run *QCPhoneProvTool.exe* to schedule CEK. (*QCPhoneProvTool.exe
    /HDCPCEK &lt;CEK file&gt;*) <span id="line-234"
    class="anchor"></span>
-   Run *QCPhoneProvTool.exe* tool to schedule DATA.
    (*QCPhoneProvTool.exe /HDCPData &lt;DATA file&gt;*) <span
    id="line-235" class="anchor"></span>
-   You should see on the device under **c:\\DPP\\QCOM** 2 new files:
    *HDCPCEK.PROVISION* and *HDCPDATA.PROVISION* <span id="line-236"
    class="anchor"></span>
-   Here is an example (Connected to 8994 device via telnet): <span
    id="line-237" class="anchor"></span><span id="line-238"
    class="anchor"></span><span id="line-239"
    class="anchor"></span><span id="line-240"
    class="anchor"></span><span id="line-241"
    class="anchor"></span><span id="line-242"
    class="anchor"></span><span id="line-243"
    class="anchor"></span><span id="line-244"
    class="anchor"></span><span id="line-245"
    class="anchor"></span><span id="line-246"
    class="anchor"></span><span id="line-247"
    class="anchor"></span><span id="line-248"
    class="anchor"></span><span id="line-249"
    class="anchor"></span><span id="line-250"
    class="anchor"></span><span id="line-251"
    class="anchor"></span><span id="line-252"
    class="anchor"></span><span id="line-253"
    class="anchor"></span><span id="line-254"
    class="anchor"></span><span id="line-255"
    class="anchor"></span><span id="line-256"
    class="anchor"></span><span id="line-257"
    class="anchor"></span><span id="line-258"
    class="anchor"></span><span id="line-259"
    class="anchor"></span><span id="line-260"
    class="anchor"></span><span id="line-261"
    class="anchor"></span><span id="line-262" class="anchor"></span>

         c:\Data\Test\bin>QCPhoneProvTool.exe /HDCPCEK HDCP2_Cek.dat
         Encrypting HDCP CEK...
         Provisioning encrypted HDCP CEK to DPP...
         Provisioning completed

         c:\Data\Test\bin>QCPhoneProvTool.exe /HDCPData HDCP2_Tsmt_Tst.dat
         Encrypting HDCP Data...
         Provisioning encrypted HDCP data to DPP...
         Provisioning completed

         c:\Data\Test\bin>dir c:\DPP\QCOM
          Volume in drive C is MainOS
          Volume Serial Number is 5CFB-BDA0

          Directory of c:\DPP\QCOM

         12/18/2014  08:17 AM    <DIR>          .
         12/18/2014  08:17 AM    <DIR>          ..
         12/05/2014  03:03 PM                 8 BT.PROVISION
         12/05/2014  03:03 PM                27 WLAN.PROVISION
         04/07/2016  12:42 PM                81 HDCPCEK.PROVISION
         04/07/2016  12:42 PM               625 HDCPDATA.PROVISION
                       4 File(s)            741 bytes
                       2 Dir(s)       7,139,328 bytes free

    <span id="line-263" class="anchor"></span>

-   **Reboot by soft reset ONLY!!** <span id="line-264"
    class="anchor"></span>
-   After reset, make sure *HDCPCEK.PROVISION* and *HDCPDATA.PROVISION*
    still exist in **c:\\DPP\\QCOM**. <span id="line-265"
    class="anchor"></span><span id="line-266" class="anchor"></span>

HDCP needs to be opened at least once for the provisioning to take
place. <span id="line-267" class="anchor"></span><span id="line-268"
class="anchor"></span>

### Using the Internal Utility {#Using_the_Internal_Utility}

<span id="line-269" class="anchor"></span>
Another way to provision the device is to use the
**[ProvApp](/ProvApp){.nonexistent}\_WoS** executable which is part of
the HDCP solution: <span id="line-270" class="anchor"></span><span
id="line-271" class="anchor"></span>

-   Place the *[ProvApp](/ProvApp){.nonexistent}\_WoS.exe* file and both
    \*.dat files (*HDCP2\_Cek.dat* and *HDCP2\_Tsmt\_Tst.dat*) on the
    device - See parts 3 and 6 of **Test setup deployment**. <span
    id="line-272" class="anchor"></span>
-   Run *[ProvApp](/ProvApp){.nonexistent}.exe*. <span id="line-273"
    class="anchor"></span>
-   Here is an example (Connected to 8994 device via telnet): <span
    id="line-274" class="anchor"></span><span id="line-275"
    class="anchor"></span><span id="line-276"
    class="anchor"></span><span id="line-277"
    class="anchor"></span><span id="line-278"
    class="anchor"></span><span id="line-279"
    class="anchor"></span><span id="line-280"
    class="anchor"></span><span id="line-281" class="anchor"></span>

         c:\Data\Test\bin>ProvApp_WoS.exe
         Starting ARM HDCP2 Provisioning Application

         Successfully provisioned CEK and provisioning data

         Successfully validated that CEK and provisioning data are provisioned

    <span id="line-282" class="anchor"></span><span id="line-283"
    class="anchor"></span>

Your device should now be provisioned as an HDCP Transmitter. <span
id="line-284" class="anchor"></span><span id="line-285"
class="anchor"></span>

Running internal tests {#Running_internal_tests}
----------------------

<span id="line-286" class="anchor"></span>
For running QA HDCP tests, you need a Windows Phone device (msm8994 or
msm8996) to act as the transmitter and a Windows PC (With at least
Windows 8.1 OS) to act as the receiver. <span id="line-287"
class="anchor"></span><span id="line-288" class="anchor"></span>

The device should be connected to the PC as described in **Connect to
Windows phone device** part in [Windows Threshold
Page](https://github.com/ARMmbed/ta-TZInfra/blob/master/docs/windows-threshold/README.md){.https}.
<span id="line-289" class="anchor"></span><span id="line-290"
class="anchor"></span>

### SW Receiver set-up {#SW_Receiver_set-up}

<span id="line-291" class="anchor"></span>
The easiest way to set-up a SW receiver is to use the SW receiver
installer which is built when compiling HDCP for SW\_Win32 <span
id="line-292" class="anchor"></span><span id="line-293"
class="anchor"></span>

\* Build a Win32 SW solution <span id="line-294"
class="anchor"></span><span id="line-295" class="anchor"></span>

1.  Open cmd. <span id="line-296" class="anchor"></span>
2.  cd to &lt;HDCP\_ROOT&gt;. <span id="line-297" class="anchor"></span>
3.  Generate project files for SW\_Win32 by running *python
    project\_builder.py -p SW\_Win32\_VS2015 config generate*. <span
    id="line-298" class="anchor"></span>
4.  Open Visual Studio 2015. <span id="line-299" class="anchor"></span>
5.  In the **Solution Platforms** dropdown choose **SW\_Win32**. <span
    id="line-300" class="anchor"></span>
6.  In the **Solution Configurations** dropdown choose
    **Release\_dynamic**. <span id="line-301" class="anchor"></span>
7.  Build the solution, the SW\_Receiver installer is built as part of
    the **[DiscretixReceiver](/DiscretixReceiver){.nonexistent}**
    project and in generated in
    **&lt;HDCP\_ROOT&gt;\\QA\_DxHDCP\_TST\\WorkspaceWOA\\[DiscretixReceiver](/DiscretixReceiver){.nonexistent}\\bin\\Release\\[DiscretixReceiver](/DiscretixReceiver){.nonexistent}.msi**.
    <span id="line-302" class="anchor"></span><span id="line-303"
    class="anchor"></span>

\* Run the SW\_Receiver installer <span id="line-304"
class="anchor"></span><span id="line-305" class="anchor"></span>

\* Run the QA Sink executable <span id="line-306"
class="anchor"></span><span id="line-307" class="anchor"></span>

1.  Open cmd. <span id="line-308" class="anchor"></span>
2.  cd to **C:\\[DiscretixReceiver](/DiscretixReceiver){.nonexistent}**.
    <span id="line-309" class="anchor"></span>
3.  Run *QA\_DxHDCP\_Sink\_SW.exe -t 0.0.0.0:1900*. <span id="line-310"
    class="anchor"></span>
4.  Now The QA Sink application is waiting for connection from the
    transmitter <span id="line-311" class="anchor"></span><span
    id="line-312" class="anchor"></span><span id="line-313"
    class="anchor"></span><span id="line-314"
    class="anchor"></span><span id="line-315"
    class="anchor"></span><span id="line-316"
    class="anchor"></span><span id="line-317"
    class="anchor"></span><span id="line-318"
    class="anchor"></span><span id="line-319"
    class="anchor"></span><span id="line-320"
    class="anchor"></span><span id="line-321"
    class="anchor"></span><span id="line-322"
    class="anchor"></span><span id="line-323"
    class="anchor"></span><span id="line-324"
    class="anchor"></span><span id="line-325"
    class="anchor"></span><span id="line-326"
    class="anchor"></span><span id="line-327"
    class="anchor"></span><span id="line-328"
    class="anchor"></span><span id="line-329" class="anchor"></span>

         C:\DiscretixReceiver>QA_DxHDCP_Sink_SW.exe -t 0.0.0.0:1900
         using virtual input buffer type
         using virtual output buffer type
         using unsecure input buffer
         using unsecure output buffer

         ----------------------------------------------------------
           ######### DISCRETIX LTD 2012 #########
           ######### HDCP RX QA_TST Application #########
           version: 2_2_133_0         ----------------------------------------------------------
         Sink Started

         RMI Started
         RMI IP: 0.0.0.0
         RMI Port: 1900

         Waiting for connection...

    <span id="line-330" class="anchor"></span><span id="line-331"
    class="anchor"></span>

### Device transmitter set-up {#Device_transmitter_set-up}

<span id="line-332" class="anchor"></span>
\* Connect to the device via telnet as described in **Connect using
Telnet** part in [Windows Threshold
Page](https://github.com/ARMmbed/ta-TZInfra/blob/master/docs/windows-threshold/README.md){.https}.
<span id="line-333" class="anchor"></span><span id="line-334"
class="anchor"></span>

\* Go to **c:\\data\\test\\bin** on the device <span id="line-335"
class="anchor"></span><span id="line-336" class="anchor"></span>

\* Run the QA Transmitter executable to run External BB tests
(*QA\_DxHDCP\_Transmitter\_WoS.exe -t &lt;HOST PC IP address&gt;:1900*)
<span id="line-337" class="anchor"></span><span id="line-338"
class="anchor"></span>

-   <span id="line-339" class="anchor"></span><span id="line-340"
    class="anchor"></span><span id="line-341"
    class="anchor"></span><span id="line-342"
    class="anchor"></span><span id="line-343"
    class="anchor"></span><span id="line-344"
    class="anchor"></span><span id="line-345"
    class="anchor"></span><span id="line-346"
    class="anchor"></span><span id="line-347"
    class="anchor"></span><span id="line-348"
    class="anchor"></span><span id="line-349"
    class="anchor"></span><span id="line-350"
    class="anchor"></span><span id="line-351"
    class="anchor"></span><span id="line-352"
    class="anchor"></span><span id="line-353"
    class="anchor"></span><span id="line-354"
    class="anchor"></span><span id="line-355"
    class="anchor"></span><span id="line-356"
    class="anchor"></span><span id="line-357"
    class="anchor"></span><span id="line-358"
    class="anchor"></span><span id="line-359"
    class="anchor"></span><span id="line-360"
    class="anchor"></span><span id="line-361"
    class="anchor"></span><span id="line-362"
    class="anchor"></span><span id="line-363"
    class="anchor"></span><span id="line-364"
    class="anchor"></span><span id="line-365"
    class="anchor"></span><span id="line-366"
    class="anchor"></span><span id="line-367"
    class="anchor"></span><span id="line-368"
    class="anchor"></span><span id="line-369"
    class="anchor"></span><span id="line-370" class="anchor"></span>

          c:\Data\Test\bin>QA_DxHDCP_Transmitter_WoS.exe -t 172.16.9.145:1900
          using shared memory input buffer type
          using shared memory output buffer type
          using unsecure input buffer
          using unsecure output buffer

          HDCP Receiver Number: 1, MANUAL set of IP and RMI Port
          RMI IP: 172.16.9.145
          RMI Port: 1900

          -------------------------------------------------------
            ######### DISCRETIX LTD 2013       #########
            ######### HDCP QA Test Application #########
            version: 2_2_133_0
            Transmitter HDCP version=3, Sink HDCP version=3
          -------------------------------------------------------
          ----------------[  Tests Menu ]------------------
           [1] - Basic Functionality
           [2] - Performance
           [3] - Reconnect
           [4] - Srm
           [5] - Rcv Base
           [6] - Converter
           [7] - [Settings]
          -----------------------------------------------------
           [T] - Run all Tests
          -------------------------------------------------


           [Z] - End of tests
          -------------------------------------------------

    <span id="line-371" class="anchor"></span><span id="line-372"
    class="anchor"></span>

\* Run the IQA Transmitter executable to run Internal BB and WB tests
(*IQA\_DxHDCP\_Transmitter\_WoS.exe -t &lt;HOST PC IP address&gt;:1900*)
<span id="line-373" class="anchor"></span><span id="line-374"
class="anchor"></span>

-   <span id="line-375" class="anchor"></span><span id="line-376"
    class="anchor"></span><span id="line-377"
    class="anchor"></span><span id="line-378"
    class="anchor"></span><span id="line-379"
    class="anchor"></span><span id="line-380"
    class="anchor"></span><span id="line-381"
    class="anchor"></span><span id="line-382"
    class="anchor"></span><span id="line-383"
    class="anchor"></span><span id="line-384"
    class="anchor"></span><span id="line-385"
    class="anchor"></span><span id="line-386"
    class="anchor"></span><span id="line-387"
    class="anchor"></span><span id="line-388"
    class="anchor"></span><span id="line-389"
    class="anchor"></span><span id="line-390"
    class="anchor"></span><span id="line-391"
    class="anchor"></span><span id="line-392"
    class="anchor"></span><span id="line-393"
    class="anchor"></span><span id="line-394"
    class="anchor"></span><span id="line-395"
    class="anchor"></span><span id="line-396"
    class="anchor"></span><span id="line-397"
    class="anchor"></span><span id="line-398"
    class="anchor"></span><span id="line-399"
    class="anchor"></span><span id="line-400"
    class="anchor"></span><span id="line-401"
    class="anchor"></span><span id="line-402"
    class="anchor"></span><span id="line-403"
    class="anchor"></span><span id="line-404"
    class="anchor"></span><span id="line-405"
    class="anchor"></span><span id="line-406"
    class="anchor"></span><span id="line-407"
    class="anchor"></span><span id="line-408"
    class="anchor"></span><span id="line-409"
    class="anchor"></span><span id="line-410"
    class="anchor"></span><span id="line-411"
    class="anchor"></span><span id="line-412"
    class="anchor"></span><span id="line-413"
    class="anchor"></span><span id="line-414"
    class="anchor"></span><span id="line-415"
    class="anchor"></span><span id="line-416"
    class="anchor"></span><span id="line-417"
    class="anchor"></span><span id="line-418"
    class="anchor"></span><span id="line-419"
    class="anchor"></span><span id="line-420" class="anchor"></span>

          c:\Data\Test\bin>IQA_DxHDCP_Transmitter_WoS.exe -t 172.16.9.145:1900
          using shared memory input buffer type
          using shared memory output buffer type
          using unsecure input buffer
          using unsecure output buffer

          HDCP Receiver Number: 1, MANUAL set of IP and RMI Port
          RMI IP: 172.16.9.145
          RMI Port: 1900

          -------------------------------------------------------
            ######### DISCRETIX LTD 2013       #########
            ######### HDCP QA Test Application #########
            version: 2_2_133_0
            Transmitter HDCP version=3, Sink HDCP version=3
          -------------------------------------------------------
          ----------------[  Tests Menu ]------------------
           [1] - Provisioning WoA
           [2] - Basic Functionality2
           [3] - Extra Tests
           [4] - Provisioning2 Repeater
           [5] - Extra Tests Repeater
           [6] - Versions Repeater
           [7] - Repeater Provisioning
           [8] - Repeater Basic Functionality
           [9] - Repeater Performance
           [B] - Repeater Srm
           [C] - Repeater Base
           [D] - Initialization
           [E] - Km_No_Stored_H_Prime
           [F] - Km_Stored_H_Prime
           [G] - Receiver_Info_RRX
           [H] - Locality
           [I] - Missing_Messages
           [J] - Pairing_Info
           [K] - Out_Of_Order
           [L] - Ake_Reset
           [M] - Repeater_Auth
           [N] - [Settings]
          -----------------------------------------------------
           [T] - Run all Tests
          -------------------------------------------------

           [Z] - End of tests
          -------------------------------------------------

    <span id="line-421" class="anchor"></span><span id="line-422"
    class="anchor"></span>

Running End-2-End tests {#Running_End-2-End_tests}
-----------------------

<span id="line-423" class="anchor"></span>
The HDCP DLL must go through a process of PE-signing by Microsoft in
order for it to work with Miracast application. <span id="line-424"
class="anchor"></span><span id="line-425" class="anchor"></span>

\* Some information about PE signing can be found here:
[https://msdn.microsoft.com/en-us/library/windows/desktop/aa376846%28v=vs.85%29.aspx?f=255&MSPPError=-2147217396](https://msdn.microsoft.com/en-us/library/windows/desktop/aa376846(v=vs.85).aspx?f=255&MSPPError=-2147217396){.https}
<span id="line-426" class="anchor"></span><span id="line-427"
class="anchor"></span>

\* Customers need to change the HLOS DLL name to
`oemhdcp.dll`{.backtick} and then PE sign it. <span id="line-428"
class="anchor"></span><span id="line-429" class="anchor"></span>

HDCP Logging {#HDCP_Logging}
------------

<span id="line-430" class="anchor"></span>
HDCP logs on Windows Phone can be viewed in 3 ways: <span id="line-431"
class="anchor"></span><span id="line-432" class="anchor"></span>

1.  **Log files** <span id="line-433" class="anchor"></span>

    -   HDCP logs are written to files with **HDCP\_TSMT** prefix
        located in **c:\\data\\test\\bin** (or what is given as the
        **[LogPath](/LogPath){.nonexistent}** configuration in the
        transmitter's configuration file). <span id="line-434"
        class="anchor"></span><span id="line-435"
        class="anchor"></span><span id="line-436"
        class="anchor"></span><span id="line-437" class="anchor"></span>

        <div class="important">

        <span id="line-1-4" class="anchor"></span>
        -   This capability is enabled ONLY when running
            release executables. <span id="line-2-3"
            class="anchor"></span>
        -   **[EnableLogs](/EnableLogs){.nonexistent}** configuration
            must be set to **True**.

        </div>

        <span id="line-438" class="anchor"></span>

    Note: You may get them using 'getd' commands, see "Basic Power shell
    commands" in [Windows Threshold
    Page](https://github.com/ARMmbed/ta-TZInfra/blob/master/docs/windows-threshold/README.md){.https}.
    <span id="line-439" class="anchor"></span><span id="line-440"
    class="anchor"></span>

2.  **Standard output** <span id="line-441" class="anchor"></span>

    -   HDCP logs are written to standard output so they are shown in
        the telnet window. <span id="line-442"
        class="anchor"></span><span id="line-443"
        class="anchor"></span><span id="line-444" class="anchor"></span>
        <div class="important">

        <span id="line-1-5" class="anchor"></span>
        -   **[StdoutLogs](/StdoutLogs){.nonexistent}** configuration
            must be set to **True**.

        </div>

        <span id="line-445" class="anchor"></span>

3.  **[WinDbg](/WinDbg){.nonexistent}** <span id="line-446"
    class="anchor"></span>

    -   HDCP logs are forwarded to the Windows debugger, this is
        relevant only when running the tests executables with
        [WinDbg](/WinDbg){.nonexistent}. <span id="line-447"
        class="anchor"></span><span id="line-448"
        class="anchor"></span><span id="line-449"
        class="anchor"></span><span id="line-450" class="anchor"></span>

        <div class="important">

        <span id="line-1-6" class="anchor"></span>
        -   This capability will harm performance drastically so it is
            not advised. <span id="line-2-4" class="anchor"></span>
        -   **[WinDbgLogs](/WinDbgLogs){.nonexistent}** configuration
            must be set to **True**.

        </div>

        <span id="line-451" class="anchor"></span><span id="line-452"
        class="anchor"></span>

Packaging {#Packaging}
---------

<span id="line-453" class="anchor"></span>
In order to create a release package for customers, you can use the
*create\_hdcp\_package\_win.py* utility located in
**&lt;HDCP\_ROOT&gt;\\HDCP**. <span id="line-454"
class="anchor"></span><span id="line-455" class="anchor"></span>

Run *create\_hdcp\_package\_win.py -h* for help. <span id="line-456"
class="anchor"></span><span id="line-457" class="anchor"></span>

For example, *python create\_hdcp\_package\_win.py -p WoS\_ARM\_VS2015
-s WoaTZ4\_0 --tz-platforms-root c:\\Projects\\TZPlatforms --qc-release
01700.1a* will create a release package for msm8996 devices based on QC
release 01700.1a. <span id="line-458" class="anchor"></span><span
id="line-459" class="anchor"></span>

The packaging script will create 3 zip files: <span id="line-460"
class="anchor"></span><span id="line-461" class="anchor"></span>

1.  **DxHDCP.zip** - The inner HDCP package (given to customers) in
    **&lt;HDCP\_ROOT&gt;\\HDCP**. <span id="line-462"
    class="anchor"></span>
2.  **DxHDCPPackage.zip** - The outer HDCP package (NOT given
    to customers) in **&lt;HDCP\_ROOT&gt;\\HDCP**. <span id="line-463"
    class="anchor"></span>
3.  **QA\_TST.zip** - The QA package (given to customers) in
    **&lt;HDCP\_ROOT&gt;\\QA\_DxHDCP\_TST\\WorkspaceWOA**. <span
    id="line-464" class="anchor"></span>

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
