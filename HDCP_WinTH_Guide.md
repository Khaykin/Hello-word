#HDCP_WinTH_Guide

##Contents:
- [HDCP on Windows Threshold (Windows 10)](#hdcp-on-windows-threshold-(windows-10))
- [Development Environment Prerequisite](#development-environment-prerequisite)
- [Supported platforms](#supported-platforms)
- [Building the project](#building-the-project)
- [Git information](#git information)
- [Environment](#environment)
- [Build steps](#build steps)
- [Test setup deployment](#test-setup-deployment)
- [Provisioning](#provisioning)
- [Using QC Tool](#using-qc-tool)
- [Using the Internal Utility](#using-the-internal-utility)
- [Running internal tests](#running-internal-tests)
- [SW Receiver set-up](#sw-receiver-set-up)
- [Device transmitter set-up](#device-transmitter-set-up)
- [Running End-2-End tests](#running-end-2-end-tests)
- [HDCP Logging](#hdcp-logging)
- [Packaging](#packaging)

## HDCP on Windows Threshold (Windows 10)

 - This page describes how to build a testing setup for HDCP on Windows 10 platforms. 

## Development Environment Prerequisite

- For Windows 10 Development Environment see **Development Environment
Check List** and **Windows 10 Toolchain Setup** parts in [Windows
Threshold
Page](https://github.com/ARMmbed/ta-TZInfra/blob/master/docs/windows-threshold/README.md)

##Supported platforms

- Qualcomm's msm8994 
- Qualcomm's msm8996

## Building the project

### Git information 

 - Еmplacement of branch for DxHDCP_for_Windows_Threshold is on [Github](https://github.com/ARMmbed/ta-DxHDCP/tree/DxHDCP_for_Windows_Threshold).
   
### Environment

- The project is built using Visual Studio 2013 for msm8994 platform 
- Visual Studio 2015 used for build msm8996 platform 
- Clone the HDCP repository from [GitHub](https://github.com/ARMmbed/ta-DxHDCP) to your **<HDCP_ROOT>** directory 
- Checkout the **DxHDCP_for_Windows_Threshold** branch.
- Generate the HDCP project files 
  -  Open cmd 
  - cd to <HDCP_ROOT>
  - To generate project files run:
  - **msm8994 (Visual Studio 2013)**

  ```
  python project_builder.py -p WoS_ARM_VS2013 config generate --TZ_PLATFORMS_ROOT=<Location of TZPlatforms> --PLAT_QC_WOS_GIT_REPO_TEMPLATE={qc_platform}_amss_device --PLAT_QUALCOMM_WA_PLATFORM=msm8994-wp-1-0 --PLAT_QUALCOMM_WA_QC_RELEASE=1073.1 --TZ_VERSION=3.0
  ```                                   

  - **msm8996 (Visual Studio 2015)**

  ```
 python project_builder.py -p WoS_ARM_VS2015 config generate --TZ_PLATFORMS_ROOT=<Location of TZPlatforms> --PLAT_QC_WOS_GIT_REPO_TEMPLATE={qc_platform}_tzap_dev --PLAT_QUALCOMM_WA_PLATFORM=msm8996-wp-1-0 --PLAT_QUALCOMM_WA_QC_RELEASE=01700.1a --TZ_VERSION=4.0
  ```
 
 - The current msm8996 device HW available (DXSN 2573) forces us to
   build with QC build release 01700.1a
 - If building for a different HW, need to check which QC build
   release should be used and set the
   **PLAT_QUALCOMM_WA_QC_RELEASE** flag accordingally.
 - For example: **--PLAT_QUALCOMM_WA_QC_RELEASE=42000.1**
 - You now have an updated Visual Studio solution file `DxHDCP_<2013/2015>.sln` under `<HDCP_ROOT>_build_vs<2013/2015>` and a shortcut   to it under <HDCP_ROOT>

### Build steps 

-   Open Visual Studio (2013/2015)
-   In the **Solution Configurations** dropdown choose
   **Release_dynamic** or **Debug_dynamic**. 
-   Build the solution, it will build both HLOS and TZ binaries
    (including the postbuild phase) as well as the test executables.
-   Build products information (For Release_dynamic solution
    configuration, TZ compiled with test keys):

    |                    |msm8994 (Visual Studio 2013)                    |msm8996 (Visual Studio 2015)|
    ---------------------|------------------------------------------------|--------------------------------
    HLOS products Location| \_build_vs2013\WoS_ARM-120-Release_dynamic     |\_build_vs2015\WoS_ARM-140-Release_dynamic
    HDCP HLOS library     |DxHdcp_WP10_vc120_Mt.dll                        |DxHdcp_WP10_vc140_Mt.dll                   
    Test executables | QA_DxHDCP_Transmitter_WoS.exe, IQA_DxHDCP_Transmitter_WoS.exe | QA_DxHDCP_Transmitter_WoS.exe, IQA_DxHDCP_Transmitter_WoS.exe
    Internal Provisioning utility | ProvApp_WoS.exe                         | ProvApp_WoS.exe
    TZ products Location | <HDCP_ROOT>\_build | <HDCP_ROOT>\_build
    TZ HDCP library (postbuild input)|dxhdcp2-release-Tst.lib | dxhdcp2-release-Tst.lib  
    TZ HDCP app (postbuild output) | dxhdcp2-release-Tst-msm8994-wp-1-0-1073.1.mbn | dxhdcp2-release-Tst-msm8996-wp-1-0-01700.1a.mbn
    
 - If you wish to skip the postbuild phase add **--TRUSTZONE_SKIP_POSTBUILD=True** to the project generation
    command (project_builder.py), the TZ build will now stop after
    creating the .lib file. 
-   The postbuild phase clones the relevant QC source tree and checkouts
    the relevant tag. 
    -   If you already cloned the QC source tree to the appropriate
        **DX_PREFIX_PATH** it will only try to update with the server
        using *git fetch*.
    -   You can skip this update step by giving
        *--PLAT_QC_WOS_GIT_SKIP_UPDATE=true*
        to project\_builder.py. (Very helpful when working without
        internet connection). 
-   There are more parameters which can be given to this script, you can
    see them by running: **python project_builder.py -p WoS_ARM_VS2015 -h**

## Test setup deployment

-  Connect to the device using Power shell as described in the
    **Connect to Windows phone device** part in [Windows Threshold
    Page](https://github.com/ARMmbed/ta-TZInfra/blob/master/docs/windows-threshold/README.md)
-  Change remote directory to *c:\data\test\bin*.
-  Push HLOS build products to the device by running the following commands:

```
  putd DxHdcp_WP10_vc140_Mt.dll .
  putd IQA_DxHDCP_Transmitter_WoS.exe .
  putd QA_DxHDCP_Transmitter_WoS.exe .
  putd ProvApp_WoS.exe .
  
```
  
  
  - The expected output should be as follows:
 
```
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
  
```

  -  Push TZ application (.mbn file) to the device by following the steps
  as described in the **Mass Storage mode** part in [Windows Threshold
  Page](https://github.com/ARMmbed/ta-TZInfra/blob/master/docs/windows-threshold/README.md)
  (Example below on msm8994 device already in FFU mode). 


```
  \\qnap\shared\CP\HWA\WindowsThreshold\Qualcomm\Burn_and_config_Tools>ffutool -massStorage
  Success, device resetting to mass storage mode.

  \\qnap\shared\CP\HWA\WindowsThreshold\Qualcomm\Burn_and_config_Tools>"tzapps partition\find_tzapps_partition.bat"
  Found TZAPPS in \\?\harddisk1partition24\\tzapps\

 REM Copy the .mbn file as dxhdcp2.mbn to the folder found in previous step.
 \\qnap\shared\CP\HWA\WindowsThreshold\Qualcomm\Burn_and_config_Tools>copy "C:\tmp\__build\dxhdcp2-release-Tst-msm8994-wp-1-0-1073.1.mbn" \\?\harddisk1partition24\\tzapps\dxhdcp2.mbn
 1 file(s) copied.

  \\qnap\shared\CP\HWA\WindowsThreshold\Qualcomm\Burn_and_config_Tools>dir \\?\harddisk1partition24\\tzapps
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

```

 -  Push Transmitter's configuration file to the device as  *Dx_Tsmt_HDCP.cfg*


```
  DEVICE c:\data\test\bin
  PS C:\Projects\DxHDCP_for_Windows_Threshold\__build_vs2015\WoS_ARM-140-Release_dynamic> putd ..\..\HDCP\external\HDCP_API\DxHDCP_WoS.cfg Dx_Tsmt_HDCP.cfg
  C:\Projects\DxHDCP_for_Windows_Threshold\HDCP\external\HDCP_API\DxHDCP_WoS.cfg
  1 file(s) copied to device.

```


  -  Push *HDCP2_Cek.dat* and *HDCP2_Tsmt_Tst.dat* from
    **<HDCP\_ROOT>\QA_DxHDCP_TST\ProvisioningFolder** to device, these files are input for the internal Provisioning
    utility (ProvApp_WoS.exe)
 

```
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
  
```


  -  Push **Test_Data** and **ProvisioningFolder** directories from **<HDCP_ROOT>\QA_DxHDCP_TST** to the device at `c:\data`


```

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
  
```


## Provisioning 

- There are 2 ways to provision a QC WindowsPhone device, one with a tool
  supplied by Qualcomm and the other with an internal utility supplied by us. 
- **Note:** msm8996 devices using QC release 01700.1a must use the internal
  provisioning utility due to bugs in the QC tool in the release.

## Using QC Tool 

- The official way to provision a QC WindowsPhone device is to use the QC tool **QCPhoneProvTool**.
- Here the CEK & data are stored into a special partition (DPP) and at the
  UEFI boot stage passed to the HDCP TrustZone
- This happens on every boot. 

  - Copy *QCPhoneProvTool.exe* from QC's tree to the device at `c:\data\test\bin`
   - **Location for 8994:**
      `C:\Git\msm8994-wp-1-0_amss_device\WP\prebuilt\8994\app\FactoryTools\QCPhoneProvTool`
    - **Location for 8996:**
        `C:\Git\msm8996-wp-1-0_tzap_dev\WP\prebuilt\8996\app\FactoryTools\QCPhoneProvTool`
-   Copy *HDCP2_Cek.dat* and *HDCP2_Tsmt_Tst.dat* to the device - See
    part 6 of **Test setup deployment**. 
-   Run `QCPhoneProvTool.exe` to schedule CEK. (*QCPhoneProvTool.exe
    /HDCPCEK<CEK file>*)
-   Run `*QCPhoneProvTool.exe*` tool to schedule DATA.
    (*QCPhoneProvTool.exe /HDCPData<DATA file>*) 
-   You should see on the device under **c:\DPP\QCOM** 2 new files:
    **HDCPCEK.PROVISION** and **HDCPDATA.PROVISION** 
-   Here is an example (Connected to 8994 device via telnet): 


```
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
 
```


 - **Reboot by soft reset ONLY!!** 
 - After reset, make sure **HDCPCEK.PROVISION** and **HDCPDATA.PROVISION** still exist in **c:\DPP\QCOM**. 
 - HDCP needs to be opened at least once for the provisioning to take place. 


 ## Using the Internal Utility

 - Another way to provision the device is to use the **ProvApp_WoS** executable which is part of
 the HDCP solution: 
 - Place the `ProvApp_WoS.exe` file and both *.dat files (`HDCP2_Cek.dat` and `HDCP2_Tsmt_Tst.dat`) on the
     device - See parts 3 and 6 of **Test setup deployment**.
 -   Run `ProvApp.exe`
 -   Here is an example (Connected to 8994 device via telnet):
  
```
  c:\Data\Test\bin>ProvApp_WoS.exe
  Starting ARM HDCP2 Provisioning Application

  Successfully provisioned CEK and provisioning data

  Successfully validated that CEK and provisioning data are provisioned
  
```

 - Your device should now be provisioned as an HDCP Transmitter.

 ## Running internal tests

 - For running QA HDCP tests, you need a Windows Phone device (msm8994 or msm8996) to act as the transmitter and a Windows PC (With at least Windows 8.1 OS) to act as the receiver.
 - The device should be connected to the PC as described in **Connect to Windows phone device** part in [Windows Threshold Page](https://github.com/ARMmbed/ta-TZInfra/blob/master/docs/windows-threshold/README.md)

 ## SW Receiver set-up 

 - The easiest way to set-up a SW receiver is to use the SW receiver
  installer which is built when compiling HDCP for SW_Win32
 - * Build a Win32 SW solution 
   -  Open cmd
   -  cd to <HDCP_ROOT>
   -  Generate project files for SW_Win32 by running `python project_builder.py -p SW_Win32_VS2015 config generate`
   -  Open Visual Studio 2015. 
   -  In the **Solution Platforms** dropdown choose **SW_Win32**
   -  In the **Solution Configurations** dropdown choose **Release_dynamic**
   -  Build the solution, the SW_Receiver installer is built as part of the **DiscretixReceiver** project and generated in:
     **<HDCP_ROOT>\QA_DxHDCP_TST\WorkspaceWOA\DiscretixReceiver\bin\Release\DiscretixReceiver.msi**.
 - * Run the SW_Receiver installer
 - * Run the QA Sink executable 
   -  Open cmd
   - `cd C:\DiscretixReceiver`
   -  Run `QA_DxHDCP_Sink_SW.exe -t 0.0.0.0:1900`
 -  Now The QA Sink application is waiting for connection from the transmitter


```
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
  
 ```
 
## Device transmitter set-up

- Connect to the device via telnet as described in **Connect using Telnet** part in [Windows Threshold
Page](https://github.com/ARMmbed/ta-TZInfra/blob/master/docs/windows-threshold/README.md)
- Go to `c:\data\test\bin` on the device
- Run the QA Transmitter executable to run External BB tests `QA_DxHDCP_Transmitter_WoS.exe -t <HOST PC IP address>:1900`

```
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

```

 - Run the IQA Transmitter executable to run Internal BB and WB tests `IQA_DxHDCP_Transmitter_WoS.exe -t <HOST PC IP address>:1900`


```
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
  
```

## Running End-2-End tests 

The HDCP DLL must go through a process of PE-signing by Microsoft in
order for it to work with Miracast application.
- Some information about PE signing can be found [here]
(https://msdn.microsoft.com/en-us/library/windows/desktop/aa376846%28v=vs.85%29.aspx?f=255&MSPPError=-2147217396).
- Customers need to change the HLOS DLL name to `oemhdcp.dll` and then PE sign it.

## HDCP Logging

- HDCP logs on Windows Phone can be viewed in 3 ways: 
  -  **Log files** 
    -   HDCP logs are written to files with **HDCP_TSMT** prefix
        located in **c:\data\test\bin** (or what is given as the
        **LogPath** configuration in the
        transmitter's configuration file).
        -   This capability is enabled ONLY when running release executables. 
        -   **EnableLogs** configuration must be set to **True**.

    - **Note:** You may get them using 'getd' commands, see "Basic Power shell commands" in [Windows Threshold
    Page](https://github.com/ARMmbed/ta-TZInfra/blob/master/docs/windows-threshold/README.md)
-  **Standard output** <span id="line-441" class="anchor"></span>
    -   HDCP logs are written to standard output so they are shown in
        the telnet window.         
    -   **StdoutLogs** configuration must be set to **True**.

-  **WinDbg** 
    -   HDCP logs are forwarded to the Windows debugger, this is
        relevant only when running the tests executables with WinDbg.
        -   This capability will harm performance drastically so it is not advised.
        -   **WinDbgLogs** configuration must be set to **True**.

## Packaging

- In order to create a release package for customers, you can use the `create_hdcp_package_win.py` utility located in
**<HDCP_ROOT>\HDCP**
- Run `create_hdcp_package_win.py -h` for help.
- For example: `python create_hdcp_package_win.py -p WoS_ARM_VS2015 -s WoaTZ4_0 --tz-platforms-root c:\Projects\TZPlatforms --qc-release 01700.1a` will create a release package for msm8996 devices based on QC release 01700.1a.


1.  **DxHDCP.zip** - The inner HDCP package (given to customers) in **<HDCP_ROOT>\HDCP**.
2.  **DxHDCPPackage.zip** - The outer HDCP package (NOT given to customers) in <HDCP_ROOT>\HDCP**. 
3.  **QA_TST.zip** - The QA package (given to customers) in
    **<HDCP_ROOT>\QA_DxHDCP_TST\WorkspaceWOA**.
