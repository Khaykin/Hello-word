#DxHDCP readme

##General
This project implements HDCP 2.2 Interface Independent Adaptation (IIA) protocol.  
In order to reach high security, security sensitive logic is running inside HW assisted Trusted Execution Environment. More information is here: `\\qnap\shared\Lectures\HWA\HWA-Platforms Introductions by Dima.heb.avi`   
Specification, Errata and Compliance Test Specification (CTS) can be found <a href="http://digital-cp.com/hdcp-specifications/">In the DCP site</a>  
This project depends on: <a href="https://github.com/ARMmbed/ta-TZInfra">TZInfra</a>, <a href="https://github.com/ARMmbed/ta-Vos6">VOS</a> and <a href="https://github.com/ARMmbed/ta-Infra">DxInfra</a> libraries.
* TZInfra library introduction is <a href="docs/internal/TZInfra\TZInfra%20Introduction.pptx"> here</a>
* Recorded lectures related to TZInfra library are saved under `\\qnap\shared\Lectures\TZinfra`
* Recorded lectures related to VOS library are saved under `\\qnap\shared\Lectures\VOS`
* Recorded lectures related to DxInfra library are saved under `\\qnap\shared\Lectures\DXInfra`
* Explanation of entire HDCP ecosystem can be found here: `\\qnap\shared\Lectures\HDCP\HDCP ecosystem overview by Dima.heb.avi`
* Explanation of HDCP protocol can be found <a href="docs/internal/Introduction%20to%20the%20HDCP%20Protocol.pptx">here</a>, <a href="docs/internal/Introduction%20to%20the%20HDCP%20Protocol%20(version%202.2)%20-%20May%202016.pptx">here</a> and here: `\\qnap\shared\Lectures\HDCP\HDCP Spec Explanation by Gil.heb.avi`
* Development can be done on Linux Ubuntu 12/14 PC or on Windows 8.1 with Visual Studio 2015 Update 2 (or later).
* Status of supported platforms, list of upcoming deliveries can be found <a href="http://teamsites.arm.com/sites/IOTBU/Engineering/Shared Documents/Trustlets">here</a> 
* Open source
  - All open source code that used by HDCP project (including external components like TZInfra) should be approved by legal team.
  - List of open source code can be found <a href="docs/internal/open_source/">here</a> 
* Project wiki page is <a href="http://confluence.arm.com/display/taHDCP/">here</a>. For now it is empty.

##Git working procedure
Git working procedure is described
<a href="docs/internal/Git%20working%20procedures%20for%20common%20use%20cases.docx">here</a>.

##Code review
Code review is mandatory for each commit to the MDB, Long term branch or Release branch (see Git working procedure above).
Code review should be done using: <a href="http://reviewboard.discretix.com/">review board server</a>.
For more information, see <a href="http://172.16.7.200/CP/PRODUCTS/HA/TOOLS/ReviewBoard/">review board wiki page</a>.

##Documentation
* Documentaiton is stored into <a href="docs/">github repository docs folder</a> or into <a href="http://teamsites.arm.com/sites/IOTBU/Engineering/EngineeringGroupGrinbergDmitry">SharePoint server</a>. An instructions how to use SharePoint is <a href="http://teamsites.arm.com/sites/spsupport/SitePages/Home.aspx">here</a>
* Design documents can be found <a href="docs/internal/Design/">here</a>
* An explanation (by <a href="http://www.digital-cp.com/">DCP</a>) of compatibility issues related to HDCP repeaters with zero device count is <a href="docs/internal/plugfest042005.pdf">here</a>
* HDCP over Qualcomm platform running Windows Phone is done into <a href="https://github.com/ARMmbed/ta-DxHDCP/tree/DxHDCP_for_Windows_Threshold">Windows Phone branch</a>. The relevant wiki page is <a href="http://172.16.7.200/CP/PRODUCTS/HA/KB/HDCP_WinTH_Guide">here</a>.
* Design document for White Box tests is <a href="docs/internal/Design/HDCP_WB_redesign.docx">here</a>. Note: Currently this tests package is used only into <a href="https://github.com/ARMmbed/ta-DxHDCP/tree/DxHDCP_for_Windows_Threshold">Windows Phone branch</a>.  
* High level test plan is <a href="docs/internal/HDCP%20high%20level%20test%20plan.docx">here</a>.
* Recorded lectures are saved under `\\qnap\shared\Lectures\HDCP`
* External HDCP documentation can be found <a href="docs/deliverables">here</a>
* Release notes for external releases stored in the <a href="http://master/">SharePoint</a> server under <a href="http://master/RnD/Products/Forms/AllItems.aspx?RootFolder=%2FRnD%2FProducts%2FCP%2FPS%2FRelease%20Notes%2FHDCP">RnD > Products > CP > PS > Release Notes > HDCP</a> 

##Copyright disclaimer
  - All new files ("C" files, "H" files, scripts, etc...) should have copyright disclaimer on the beginning of each file
  - Copyright disclaimer should be:   
`Copyright (C) 2016 ARM Ltd (or its subsidiaries).`   
`All Rights Reserved`
  - Copyright disclaimer should specify each year the code was changed in, for example if code was changed in 2015 and 2016 the copyright disclaimer should include year range:   
`Copyright (C) 2015-2016 ARM Ltd (or its subsidiaries).`   
`All Rights Reserved`
  - It is not mandatory to change change Discretix copyright disclaimer of existing files to new ARM copyright disclaimer

##Project tree structure
| Directory | Comment |
|----------|----------------------|
| <a href="HDCP">HDCP</a> | HDCP project root folder |
| <a href="HDCP/BaseLayer">HDCP/BaseLayer</a> | HLOS code |
| <a href="HDCP/IFLayer">HDCP/IFLayer</a> | HLOS external API layer |
| <a href="HDCP/TZService">HDCP/TZService</a> | TEE code |
| <a href="HDCP/external/HDCP_API">HDCP/external/HDCP_API</a> | External APIs and configuration files |
| <a href="HDCP/external/PlatformUtils/Common/Drmversion">HDCP/external/PlatformUtils/Common/Drmversion</a> | Product version definition and version handling code |
| <a href="HDCP/tools">HDCP/tools</a> | Tools, Provisioning binary files, Provisioning PC tool |
| <a href="QA_DxHDCP_TST">QA_DxHDCP_TST</a> | HDCP tests root folder |
| <a href="Scripts">Scripts</a>| Build and automation scripts |
| <a href="DxInfra">DxInfra</a>| External DxInfra library |
| <a href="TZInfra">TZInfra</a>| External TZInfra library |
| <a href="Vos6">Vos6</a>| External VOS library |
| <a href="docs">docs</a>| Documentation |

##Automatic system tests
* We have 3 types of automatic system tests:
  - BB (Black Box tests). These tests are part of the external releases.
  - IBB (Internal Black Box tests). Additional tests for internal use.
  - WB (White Box tests). Internal black box tests. Used mostly for CTS coverage. 
* Automated tests presentation can be found <a href="docs/internal/HDCPQA.pptx">here</a>.
* An explanation how to test new HDCP version using the Automatic test application is <a href="docs/internal/BUILDING%20HDCP%20QA%20PACKAGE.docx">here</a>.
* HDCP tests require stable bidirectional ping of 4 or less miliseconds. In order to achieve this, need to do the following steps:
  - Connect device to PC using USB tethering. In this case it is possible to run HDCP tests on PC against device.
  - Connect two devices using Wi-Fi direct.
  - Connect two devices using Wi-Fi - one device can be a Wi-Fi hotspot and another device can connect to it. Wi-Fi power saving mode should be turned off. For Qualcomm devices the following values should be changed in `WCNSS_qcom_cfg.ini` as follows: `gEnableBmps=0`, `gEnableImps=0` and `gDot11Mode=3`
    1. This file can be found in the following paths inside device: `/data/misc/wifi/`, `/system/etc/firmware/wlan/qca_cld/` or `/system/etc/wifi/`
    2. If not set - pull this file, change only this specific values and push back to device.
    3. Make sure that when changing this file, file permissions, user and group of this file should be not changed.
    4. When Wi-Fi configuration is finished, make sure that all Wi-Fi configuration dialogs are closed.
 - Prevent device under test from entering sleep or power save mode. For some devices (Qualcomm devices and maybe additional devices) need to touch device screen periodically. For that purpose you may use the following scripts: <a href="Scripts/ScreenOnOff.sh">ScreenOnOff.sh</a> and <a href="Scripts/android_keep_devices_busy.sh">android_keep_devices_busy.sh</a> to simulate this. 

##HDCP and tests compilation
  - Before compilation of HDCP project, all SW components and tools required for TZInfra library compilaiton should be installed. List of these requirements can be found in readme files inside <a href="https://github.com/ARMmbed/ta-TZInfra">root TZInfra directory</a>.
  - Also, make sure that:
    * export TZ_PLATFORMS_ROOT is defined in .bashrc: `export TZ_PLATFORMS_ROOT=/mnt/TZPlatforms/`
    * `alias sudo='sudo env PATH=$PATH'` is in .bashrc. This alias needed since on Ubuntu sudo doesn't define PATH.
  - Scripts are located under <a href="Scripts">Scripts</a> folder.
  - Compilation script: `build_hdcp_and_tests.py`. Run this script with `-h` flag in order to see help menu.

##HDCP and tests installation and running tests
  - In order to push files to device, USB configuration should be set to MTP. In the original Qualcomm MSM8996 image, when the device reboot – the USB configuration goes back to “charging” even if you set it to MTP before the reboot. 
    To fix this do the following steps:
    * Connect to device to the PC using USB cable and execute the following commands in the terminal:
      - `adb root`
      - `adb shell setprop persist.sys.usb.config mtp,adb`
      - `adb reboot`
    * When device starts, on the Android UI go to `Settings` -> `Developer Options` -> `Select USB Configuration` menu and make sure that `Select USB Configuration` option is set to `MTP (Media Transfer Protocol)`.
  - Scripts are located under <a href="Scripts">Scripts</a> folder.
  - Script that install HDCP and tests to the connected device or Linux PC: `install_hdcp_and_tests.py`. Run this script with `-h` flag in order to see help menu. 
  - `run_all_permutations_linux_linux.sh` - run all tests on Linux PC (Sink and Source are running on the same Linux PC). This script does not require any command line parameters.
  - `run_all_permutations_linux_qualcomm.sh` - run all tests on Linux PC against Qualcomm device. This script does not require any command line parameters.
    * Sink running on Linux PC and Source on Qualcomm device that connected to the Linux PC using USB cable.
    * Source running on Linux PC and Sink on Qualcomm device that connected to the Linux PC using USB cable.
  - `run_all_permutations_qualcomm_qualcomm.sh` - Two Qualcomm devices should be connected to the Linux PC. One device running Sink, second device running Source. Run this script with `-h` flag in order to see help menu.
  - When using `run_all_permutations_linux_linux.sh` or `run_all_permutations_linux_qualcomm.sh` scripts, the `net.ipv4.tcp_slow_start_after_idle` parameter should be set to `0` into `/etc/sysctl.conf` file. In order to do that, need to edit `/etc/sysctl.conf` file (with sudo) and add `net.ipv4.tcp_slow_start_after_idle = 0` line at end of this file. In order enforce OS to read updated file, execute: `sudo sysctl -p` command or reboot the PC.

##HDCP compilation and run on Linux PC
* Compilaiton and perparation steps:
```
rm -rf /tmp/hdcp                                #delete SFS & HDCP config files from previous build/run
cd Scripts
./build_hdcp_and_tests.py -p SW_Linux32         #add "-b debug" flag for debug compilation
./install_hdcp_and_tests.py -p SW_Linux32       #add "-b debug" flag for debug compilation
cd Linux32_SW_hdcp_devices
```
* Steps for Source side:
```
cd Devices/TransmitterRelease                   # TransmitterDebug directory for debug run
export LD_LIBRARY_PATH=$LD_LIBRARY_PATH:${PWD}
./QA_WB_DxHDCP_Transmitter_SW -t 127.0.0.1:1900 # Source side tests executable, can be:
                                                # IQA_DxHDCP_Transmitter_SW (IBB - Internal Black Box)
                                                # or QA_DxHDCP_Transmitter_SW (BB - Black Box)
                                                # or QA_WB_DxHDCP_Transmitter_SW (WB - White box).
                                                # If running Sink and Source on a different PCs,
                                                # instead of 127.0.0.1 an IP address of Source machine
                                                # should be used
```
* Steps for Sink side (Source and Sink sides should run in a separate shell tabs):
```
cd Devices/ReceiverRelease                      # ReceiverDebug directory for debug run
export LD_LIBRARY_PATH=$LD_LIBRARY_PATH:${PWD}
./QA_WB_DxHDCP_Sink_SW -t 127.0.0.1:1900        # Sink side execubtalbe, Can be:
                                                # QA_DxHDCP_Sink_SW (sink executable for IBB and BB tests)
                                                # or QA_WB_DxHDCP_Sink_SW (sink executable for WB tests)
                                                # If running Sink and Source on a different PCs,
                                                # instead of 127.0.0.1 an IP address of Source machine
                                                # should be used
```
##HDCP traffic analysis
* In order to debug HDCP stack with HDCP tests or end to end tests against 3rd party equipment, it is possible to record HDCP traffic using `tcpdump` utility and analyze recorded traffic using <a href="https://www.wireshark.org/">Wireshark</a> application:
  - Wireshark can be installed on both: Linux and Windows PC. It is recommended to install and use it on Windows PC.
  - After Wireshark installation, HDCP2 trafic analysis should be enabled by entering: `Analyze`->`Enabled Protocols...` menu and checking options `HDCP2` and `hdcp2_tcp` as described below: ![GitHub Logo](docs/images/WireSharkCfg1.jpg)
* `tcpdump` utility can be used on HDCP Sink device, HDCP Source device or on both devices
* Root permissions is required in order to use `tcpdump` utility
* For Linux Ubuntu PCs, `tcpdump` utility should be installed by `apt-get install tcpdump` command
* For Android devices, `tcpdump` for Android shoud be installed to the device:
  - It can be downloaded from <a href="http://www.androidtcpdump.com/android-tcpdump/downloads/">here</a> and pushed to the device
  - On Qualcomm devices, `tcpdump` utility is part of factroy image, installation of it is not required
  - On Mediatek decives, `MTKLogger` utility should be used for traffic analysis (see below)
* In order to capture HDCP traffic on Android device, the following steps should be done:
  - Connect device to the PC using USB cable
  - Enter ADB shell (using `adb -s <device id> shell` command)
  - Execute the following command: `tcpdump -i any -s 0 -w <file name.pcap>`. `<file name.pcap>` parameter should be replaced by actual file name where all captured traffic will be saved (e.g. `/data/tmp/capture.pcap`)
* In order to capture HDCP traffic on Linux Ubuntu PC, the following command should be used: `sudo tcpdump -s 0  -i <interface> -w <file name.pcap>`.
  - `<interface>` parameter should be replaced by network interface name through which the HDCP traffic passes
    1. `usb0` if USB tethering is used
    2. `wlan0` if Wi-Fi connection is used
    3. `eth0` if Ethernet connection is used
    4. For full list of available network interfaces, use `/sbin/ifconfig` command
  - `<file name.pcap>` parameter should be replaced by actual file name where all captured traffic will be saved (e.g. `${HOME}/capture.pcap`)
* In order to capture HDCP traffic on Mediatek device, the following steps should be done:
  - Dial `*#*#3646633#*#*` and MTK EngineerMode will pop up
  - Select `Log and debugging`
  - Select `MTKLogger`
  - Click the `Settings` button in the right-top corner on the screen switches UI will pop up
  - Check is the `NetoworkLog` is switched on and press "back"
  - Click the `Start logging` button in the center-bottom on the screen
  - Start your testing and get into the `MTKLogger` UI and click the `Stop logging` button in the center bottom on the screen
  - The netdump file will be in `/mnt/sdcard/mtklog/netlog`
  - It is possible to pull the entire log files using `adb pull /mnt/sdcard/mtklog mtklog`
 

 ##Debugging HLOS

  - In config file [DxHDCP.cfg]:
    - `EnableLogs=True` Must be true to get ANY logs in HLOS following to level of set up `DebugLevel=`.
    - `LogcatLogs=True` If True, most HLOS printouts will go into logcat. Better to use this because otherwise writing to the *.DxLog file  slows the system
  - Using debug version is possible, but due to system slowness:
    - DxHwLogTrace - These printouts are seen only on debug version
    - DxHwLogError - These printouts are seen on both release & debug versions
  - Viewing DxModule printouts:
  
  ```
  adb -s <device_id> logcat -v threadtime | grep DxModule
  ```
 - Viewing Qualcomm's printouts:
  
  ```
  adb -s <device_id> logcat -v threadtime | grep QSEE
  ```
  
  ##Debugging TEE
  
  - For enable service logging mechanism in DxHDCP.cfg set up next values to True:
    - TeeNativeLogging=True
    - TeeInternalLogging=True
  
  - Viewing entry point address:
  
  ```
  adb -s <device_id> pull /firmware/image/dxhdcp2.mdt
  readelf -h dxhdcp2.mdt (expected entry point address: 0x88e00000)
  ```
  
  
  
##HDCP release versions
* For external releases created from MDB, the version format is `2.2.X.0` where `X` - major number of the product version.
* For external releases created not from MDB, the version format is `2.2.X.Y` where `X` - major number of the product version, `Y` - major number of the product version
* Before external release compilation, major and minor numbers should be coordinated with Team Leader.
* Release version is defined by <a href="HDCP/external/PlatformUtils/Common/Drmversion/DxDrmVersionDefinitions.h">HDCP\external\PlatformUtils\Common\Drmversion\DxDrmVersionDefinitions.h</a> file.

##HDCP releases
* Before release compilation, the release version should be set by modifying <a href="HDCP/external/PlatformUtils/Common/Drmversion/DxDrmVersionDefinitions.h">HDCP\external\PlatformUtils\Common\Drmversion\DxDrmVersionDefinitions.h</a> file.
* All releases and all deliverables should be compiled using <a href="http://cp-hwa-jenkins-master:8080/view/HDCP%20projects/">Jenkins</a>
  - After each commit to GIT master, an automatic CI build tests will start
  - When modifying documents, in order to prevent automatic CI build and tests run, need to include `[ci skip]` message to the GIT comit message
* HDCP release package should include the following documentation reviewed by TW:
  - ARM TrustZone Protected HDCP Link Protection API Overview.This document includes HDCP API overview and HDCP API use case diagrams. For some HDCP releases this document can be represented by two separate documents: API overview document (generated by Doxygen) and HDCP API use cases diagrams.
  - ARM TrustZone Protected HDCP Developer Guide (this document is different for different platforms)
  - ARM TrustZone Protected HDCP Provisioning Tool User Guide
* HDCP Tests release package should include the following documentation reviewed by TW:
  - ARM TrustZone Protected HDCP Test User Guide (this document is different for different platforms)
  - ARM TrustZone Protected HDCP Test Description
* HDCP release should be uploaded to the <a href="http://releaseserver:10000/">Release server</a>. The release should include:
  - Deliverables should be uploaded to the root folder of the release:
    1. HDCP release package
    2. External QA tests package compiled for 32 bit release configuration
  - If according to the DoD, the libstagefright_hdcp source package should be included to the release, it should be uploaded to the root folder of the release.
  - Internal BB and WB tests, all logs, tests terminal captures and tcpdump outputs should be uploaded to the NOT_FOR_RELEASE folder of the release.
  - VDD document should be aligned to template and should be uploaded to the root folder of the release.
  - Jenkins build log should be uploaded to the NOT_FOR_RELEASE folder of the release.
  - The following information should be included into each release:
    1. Version number
	2. Brief description
	3. Link to Jenkins build
	4. GIT tag name
	5. If release is created not from the MDB, name of branch which was built the release

##Release testing
* Before testing, HDCP release and QA tests should be downloaded from the <a href="http://releaseserver:10000/">Release server</a>.
* Build output should be reviewed. Values of all compilation flags (OPL support/ SCP support/ HDMI support/ Generic repeaters support/ etc…) should be validated.
* HDCP package content should be checked - it should match VDD document. All necessary files should exists in the packages:
  - PDF documents:
    1. ARM TrustZone Protected HDCP Link Protection API Overview
    2. ARM TrustZone Protected HDCP Developer Guide (this document is different for different platforms)
    3. ARM TrustZone Protected HDCP Provisioning Tool User Guide
  - HLOS binaries 32 bit debug, 32 bit release, optional 64 bit debug, optional 64 bit release
  - TZ binaries: test debug, test release, production debug, production release variants
  - Include files:
    1. `DX_Hdcp_Errors.h`
    2. `Dx_Hdcp_Provisioning.h`
    3. `DX_Hdcp_Receiver.h`
    4. `DX_Hdcp_Repeater.h`
    5. `DX_Hdcp_Shared_Memory.h`
    6. `DX_Hdcp_Transmitter.h`
    7. `DX_Hdcp_Types.h`
    8. `DX_VOS_Errors.h`
    9. `DxTypes.h`
  - HDCP configuration file (<a href="HDCP/external/HDCP_API">HDCP/external/HDCP_API</a> folder includes several configuration files. Build package scripts includes right configuration file to the release package)
  - Relevant license files for open source code that used by HDCP including TZInfra and other external libraries. Licence files related to TZInfra library can be found <a href="licenses">here</a>. If new open source code will be used as part of the HDCP code, the relevant license files should be added.
  - PC provisioning application installer
  - Provisioning sample app and test source files: dxhdcpprov.cpp and DxHdcp_Provisioning_Tst.c
  - Facsimile provisioning binary files for sink (both: HDCP 2.1 and HDCP 2.2 variants)
  - Facsimile provisioning binary files for source

* External HDCP tests package content should be checked. All necessary files should exists in the packages:
  - PDF documents:
    1. ARM TrustZone Protected HDCP Test User Guide (this document is different for different platforms)
    2. ARM TrustZone Protected HDCP Test Description
  - Compiled tests binaries
  - Tests sources and make files
  - Facsimile provisioning binary files for sink (both: HDCP 2.1 and HDCP 2.2 variants)
  - Facsimile provisioning binary files for source
  - Compile tests and install scripts
  - Relevant precompiled libraries and libraries headers
  - Test vectors in a binary form
  - Postbuild scripts and source files should be taken from TZInfra (for platforms who supports it, like Qualcomm the postbuild files are <a href="https://github.com/ARMmbed/ta-DxHDCP/tree/master/TZInfra/Platforms/Qualcomm/postbuild">here</a>)
  - Configuration files (Workspace folder)

* Postbuild (for platforms supports it like Qualcomm) and installation process should be done according to the developer guide.
* Following ARM TrustZone Protected HDCP Provisioning Tool User Guide install Provisioning tool and make PM.out. A sanity test of HDCP 2.2 Sink against HDCP 2.2 Source should be done using generated PM.out file.
* All bugs that fixed in this specific release should be concluded in the BTS.
* The following configurations should be tested by BB/IBB/WB tests in release variant with test TZ app:
  - HDCP 2.2 source against HDCP 2.0/2.1/2.2 sink.
  - HDCP 2.2 sink against HDCP 2.0/2.1/2.2 source.
* The following configurations should be tested by BB/IBB/WB tests in debug variant with test TZ app:
  - HDCP 2.2 against 2.2 sanity test: only BB/init to close test.

* The following configurations should be tested against 3rd party devices (end to end tests)
  - HDCP test TZ app release version should be tested as a Source against:
    1. Cavium Dongle (HDCP 2.1) with test keys (autentication should pass and picture should be shown on the screen connected to the dongle)
  - HDCP test TZ app release version should be tested as a Sink against:
    1. Qualcomm WFD client (HDCP 2.2) with test keys (autentication should pass and picture should be shown on the screen of the source device)
  - HDCP production TZ app release version should be provisioned with test keys and tested as a Source against:
    1. Samsung AllShare Cast Dongle (HDCP 2.2) with production keys, only authentication should pass
    2. Samsung TV (HDCP 2.1) with production keys, only authentication should pass
  - HDCP production TZ app release version should be provisioned with test keys and tested as a Sink against:
    1. Qualcomm WFD client (HDCP 2.2) with test keys (autentication should pass and picture should be shown on the screen of the source device)
* The full end to end testing guide is here: <a href="docs/internal/HDCP%20End%20to%20End%20testing%20guide.docx">here</a> 
* When release is tested
  - The test summary PDF should be created and added to the external BB test package.
  - Status of the release into release server is changed to “Tested”.
