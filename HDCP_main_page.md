<div id="header">

<div>

Search:

</div>

<div id="logo">

[![MoinMoin Logo](/moin_static194/common/moinmoin.png)](/FrontPage)

</div>

<span id="pagelocation"><span class="pagepath">[CP](/CP)<span class="sep">/</span>[PRODUCTS](/CP/PRODUCTS)</span><span class="sep">/</span>[HDCP](/CP/PRODUCTS/HDCP?action=fullsearch&value=linkto%3A%22CP%2FPRODUCTS%2FHDCP%22&context=180 "Click to do a full-text search for this title"){.backlink}</span> {#locationline}
==============================================================================================================================================================================================================================================================================================================

-   [RecentChanges](/RecentChanges)
-   [FindPage](/FindPage)
-   [HelpContents](/HelpContents)
-   [CP/PRODUCTS/HDCP](/CP/PRODUCTS/HDCP)

<div id="pageline">

------------------------------------------------------------------------

</div>

</div>

<div id="page" lang="en" dir="ltr">

<div id="content" dir="ltr" lang="en">

<span id="top" class="anchor"></span> <span id="line-1"
class="anchor"></span><span id="line-2" class="anchor"></span>

HDCP product main page {#HDCP_product_main_page}
----------------------

<span id="line-3" class="anchor"></span>
The weekly sync status is located in [weekly
syncs](http://master/RnD/Projects/CP/HDCP/HDCP2.x%20Sync%20Meetings.pptx){.http}
<span id="line-4" class="anchor"></span><span id="line-5"
class="anchor"></span>

Integration and bring-up repeated issues can be found
[here](/CP/PRODUCTS/HDCP/INTEGRATION) <span id="line-6"
class="anchor"></span><span id="line-7" class="anchor"></span>

#### Expected Releases {#Expected_Releases}

<span id="line-8" class="anchor"></span>

#### DxHdcp Prerequisites {#DxHdcp_Prerequisites}

<span id="line-9" class="anchor"></span>
- ping between Transmitter device and Receiver device should take no
longer than 4 ms <span id="line-10" class="anchor"></span><span
id="line-11" class="anchor"></span>

- Wifi power saving mode should be turned off. WFD disables the power
saving mode, however QA\_TST needs power saving mode off in wifi config
file On the device. <span id="line-12" class="anchor"></span><span
id="line-13" class="anchor"></span>

On Qualcomm's platform, please modify
`/data/misc/wifi/WCNSS_qcom_cfg.ini` with the following values: <span
id="line-14" class="anchor"></span><span id="line-15"
class="anchor"></span>

-   gEnableBmps=0 <span id="line-16" class="anchor"></span>
-   gEnableImps=0 <span id="line-17" class="anchor"></span>
-   gDot11Mode=3 <span id="line-18" class="anchor"></span><span
    id="line-19" class="anchor"></span>

\
**Note**: on APQ8084 device the location of the wifi configuration file
was changed to: `/system/etc/wifi/WCNSS_qcom_cfg.ini` <span id="line-20"
class="anchor"></span><span id="line-21" class="anchor"></span>

#### TZ Application {#TZ_Application}

<span id="line-22" class="anchor"></span>
The TZ application address for HDCP is: 0x88E00000 unless defined
otherwise in specific project <span id="line-23"
class="anchor"></span><span id="line-24" class="anchor"></span>

For Project Specific address, go to the project page in:
[CP/PROJECTS](/CP/PROJECTS) <span id="line-25"
class="anchor"></span><span id="line-26" class="anchor"></span>

Location of Development guide which contains info for building the TZ
app: [DxHDCP Qualcomm Developer
Guide.pdf](http://master/RnD/Products/CP/Link%20Protection/HDCP/SW%20Documents/Deliverables/Released%20PDFs/HDCP%20Qualcomm%20Developer%20Guide%20v1.7.pdf){.http}
<span id="line-27" class="anchor"></span><span id="line-28"
class="anchor"></span>

#### HDCP Dongles {#HDCP_Dongles}

<span id="line-29" class="anchor"></span>
Info about how to change dongle properties can found here:
[CP/PRODUCTS/HDCP/DONGLES](/CP/PRODUCTS/HDCP/DONGLES) <span id="line-30"
class="anchor"></span><span id="line-31" class="anchor"></span>

#### HDCP debugging {#HDCP_debugging}

<span id="line-32" class="anchor"></span>
-   For Analyzing HDCP packets through wireshark, please enable HDCP
    protocol in wireshark. Instructions can be found
    [here](/CP/PS/TOOLS/WIRESHARK). <span id="line-33"
    class="anchor"></span><span id="line-34" class="anchor"></span>

#### Enabling WFD working with HDCP on Qualcomm Devices {#Enabling_WFD_working_with_HDCP_on_Qualcomm_Devices}

<span id="line-35" class="anchor"></span>
To enable HDCP in WFD, on qualcomm devices, there are two files in the
Qualcomm device that needs to be modified: <span id="line-36"
class="anchor"></span><span id="line-37" class="anchor"></span>

1.  In the device, under the path `/system/etc/wfdconfig.xml` there is a
    tag inside Capabilities that is called **`ContentProtection`**.
    <span id="line-38" class="anchor"></span>

    -   It has a parameter **`Valid`** ( on some platforms it is called
        **`HDCPValid`**). It should be set to 1. <span id="line-39"
        class="anchor"></span>
    -   Another parameter called **`EncryptAudio`** should be set to '1'
        if Audio should be encrypted. <span id="line-40"
        class="anchor"></span>
    -   Then push the updated `wfdconfig.xml` into `/system/etc` of the
        device <span id="line-41" class="anchor"></span>

2.  rebuilding WFD module to work and link with Dx Hdcp library: <span
    id="line-42" class="anchor"></span>
    -   in the Qcom source tree root: mkdir -p
        vendor/qcom/proprietary/wfd-noship/mm/hdcp/HDCP\_API <span
        id="line-43" class="anchor"></span>
    -   create Android.mk files in vendor/qcom/proprietary/wfd-noship/
        and vendor/qcom/proprietary/wfd-noship/mm/ that will have the
        following: <span id="line-44" class="anchor"></span>
        -   <span id="line-45" class="anchor"></span><span id="line-46"
            class="anchor"></span><span id="line-47"
            class="anchor"></span><span id="line-48"
            class="anchor"></span><span id="line-49"
            class="anchor"></span><span id="line-50"
            class="anchor"></span><span id="line-1-1"
            class="anchor"></span>
            <div class="highlight cfg">

            <div class="codearea" dir="ltr" lang="en">

            ``` {#CA-735020d9676c472db98ce37d56eba7c6e77e11c5 dir="ltr" lang="en"}
               ifeq ($(call is-vendor-board-platform,QCOM),true)
               ifneq ($(call is-board-platform,copper),true)
               include $(call all-subdir-makefiles)
               endif
               endif # TARGET_USES_WFD
            ```

            </div>

            </div>

            <span id="line-51" class="anchor"></span>
    -   copy libDxHdcp.so to vendor/qcom/proprietary/wfd-noship/mm/hdcp/
        ( it is needed for linking the wfd library) <span id="line-52"
        class="anchor"></span>
    -   copy the [DxHdcp](/DxHdcp){.nonexistent} header files to
        vendor/qcom/proprietary/wfd-noship/mm/hdcp/HDCP\_API <span
        id="line-53" class="anchor"></span>
    -   **<span class="u">Android L and above</span>** <span
        id="line-54" class="anchor"></span>

        -   create Android.mk file in
            vendor/qcom/proprietary/wfd-noship/mm/hdcp/ with the
            following: <span id="line-55" class="anchor"></span>
            -   <span id="line-56" class="anchor"></span><span
                id="line-57" class="anchor"></span><span id="line-58"
                class="anchor"></span><span id="line-59"
                class="anchor"></span><span id="line-60"
                class="anchor"></span><span id="line-61"
                class="anchor"></span><span id="line-62"
                class="anchor"></span><span id="line-63"
                class="anchor"></span><span id="line-64"
                class="anchor"></span><span id="line-65"
                class="anchor"></span>

                    LOCAL_PATH := $(call my-dir)
                    include $(CLEAR_VARS)
                    LOCAL_SRC_FILES := libDxHdcp.so
                    LOCAL_MODULE := libDxHdcp
                    LOCAL_MODULE_SUFFIX := .so
                    LOCAL_MODULE_TAGS := optional
                    LOCAL_MODULE_CLASS := SHARED_LIBRARIES
                    LOCAL_MULTILIB := 32
                    include $(BUILD_PREBUILT)

                <span id="line-66" class="anchor"></span>

        -   Build the HDCP prebuilt module: <span id="line-67"
            class="anchor"></span>
            -   <span id="line-68" class="anchor"></span><span
                id="line-69" class="anchor"></span><span id="line-70"
                class="anchor"></span><span id="line-71"
                class="anchor"></span>

                    pushd vendor/qcom/proprietary/wfd-noship/mm/hdcp/
                    mm -B
                    popd

                <span id="line-72" class="anchor"></span>

        -   **Note:** To make sure that the library has been built
            properly, you can add a warning in the source file:
            `vendor/qcom/proprietary/wfd/mm/hdcp/common/src/WFD_HdcpCP.cpp`
            <span id="line-73" class="anchor"></span>

            -   Look up `CWFD_HdcpCp::WFD_HdcpSessionInit` and add a
                warning inside `#ifdef WFD_HDCP_ENABLED`. <span
                id="line-74" class="anchor"></span>For example: <span
                id="line-75" class="anchor"></span><span id="line-76"
                class="anchor"></span><span id="line-77"
                class="anchor"></span><span id="line-78"
                class="anchor"></span><span id="line-79"
                class="anchor"></span><span id="line-80"
                class="anchor"></span><span id="line-81"
                class="anchor"></span><span id="line-82"
                class="anchor"></span><span id="line-1-3"
                class="anchor"></span>

                <div class="highlight cfg">

                <div class="codearea" dir="ltr" lang="en">

                ``` {#CA-152fbd6ddff4d80c7df025a908a2b01a667eab6b dir="ltr" lang="en"}
                #ifdef WFD_HDCP_ENABLED
                ...
                #warning WFD_HdcpSessionInit - HDCP ENABLED
                #else
                #warning WFD_HdcpSessionInit - HDCP DISABLED
                #endif //WFD_HDCP_ENABLED
                ```

                </div>

                </div>

                <span id="line-83" class="anchor"></span><span
                id="line-84" class="anchor"></span>

        -   **Note:** If COMPILE\_HDCP\_LIB will not set to true
            automaticlly as usual, that's the root cause in this case
            and happend for all 8996 projects. <span id="line-85"
            class="anchor"></span>

            -   Fix: add COMPILE\_HDCP\_LIB :=true manually. <span
                id="line-86" class="anchor"></span>

            <!-- -->

            -   <span id="line-87" class="anchor"></span><span
                id="line-88" class="anchor"></span><span id="line-89"
                class="anchor"></span><span id="line-90"
                class="anchor"></span><span id="line-91"
                class="anchor"></span><span id="line-92"
                class="anchor"></span>

                        COMPILE_HDCP_LIB := false
                        WFD_NOSHIP_HDCP_PATH  := $(LOCAL_PATH)/../../../../wfd-noship/mm/hdcp
                        WFD_INTERNAL_LIB_PATH := $(TOP)/vendor/qcom/proprietary/wfd-internal/mm/hdcp/lib
                        COMPILE_HDCP_LIB := $(shell if [[ -d $(WFD_NOSHIP_HDCP_PATH) && -d $(WFD_INTERNAL_LIB_PATH) ]] ; then echo true; fi)
                        COMPILE_HDCP_LIB :=true

                <span id="line-93" class="anchor"></span>

        -   **Rebuild** libwfdhdcpcp: <span id="line-94"
            class="anchor"></span>

            -   <span id="line-95" class="anchor"></span><span
                id="line-96" class="anchor"></span><span id="line-97"
                class="anchor"></span><span id="line-98"
                class="anchor"></span>

                    pushd vendor/qcom/proprietary/wfd/mm/hdcp/
                    mm -B
                    popd

                <span id="line-99" class="anchor"></span>

            -   **Note:** If `mm` fails due to missing dependencies,
                then try `mma` instead. <span id="line-100"
                class="anchor"></span>

        -   push libwfdhdcpcp that was built from
            `<Qcom source tree root>/out/target/product/<product name>/system/vendor/lib/libwfdhdcpcp.so`
            to `/system/lib` in the device ( on newer builds, the path
            is `/system/vendor/lib/`) <span id="line-101"
            class="anchor"></span>
        -   push libwfdhdcpcp that was built from
            `<Qcom source tree root>/out/target/product/<product name>/system/vendor/lib64/libwfdhdcpcp.so`
            to `/system/lib64` in the device ( on newer builds, the path
            is `/system/vendor/lib64/`) <span id="line-102"
            class="anchor"></span><span id="line-103"
            class="anchor"></span>

    -   **<span class="u">Before Android L</span>** <span id="line-104"
        class="anchor"></span>

        -   create Android.mk file in
            vendor/qcom/proprietary/wfd-noship/mm/hdcp/ with the
            following: <span id="line-105" class="anchor"></span>
            -   <span id="line-106" class="anchor"></span><span
                id="line-107" class="anchor"></span><span id="line-108"
                class="anchor"></span><span id="line-109"
                class="anchor"></span><span id="line-110"
                class="anchor"></span><span id="line-111"
                class="anchor"></span><span id="line-112"
                class="anchor"></span><span id="line-113"
                class="anchor"></span><span id="line-114"
                class="anchor"></span>

                       LOCAL_PATH := $(call my-dir)
                       include $(CLEAR_VARS)
                       LOCAL_SRC_FILES := libDxHdcp.so
                       LOCAL_MODULE := libDxHdcp
                       LOCAL_MODULE_SUFFIX := .so
                       LOCAL_MODULE_TAGS := optional
                       LOCAL_MODULE_CLASS := SHARED_LIBRARIES
                       include $(BUILD_PREBUILT)

                <span id="line-115" class="anchor"></span>

        -   in case the tree or libwfdhdcpcp was already built, clean
            libwfdhdcpcp: <span id="line-116" class="anchor"></span>
            -   <span id="line-117" class="anchor"></span><span
                id="line-118" class="anchor"></span>

                    <Qcom source tree root>make clean-libwfdhdcpcp

                <span id="line-119" class="anchor"></span>

        -   <span id="line-120" class="anchor"></span><span
            id="line-121" class="anchor"></span>

                <Qcom source tree root>make libwfdhdcpcp

            <span id="line-122" class="anchor"></span>

        -   push libwfdhdcpcp that was built from
            `<Qcom source tree root>\out\target\product\<product name>\system\lib\libwfdhdcpcp.so`
            to `/system/lib` in the device ( on newer builds, the path
            is `/system/vendor/lib/`) <span id="line-123"
            class="anchor"></span><span id="line-124"
            class="anchor"></span>

You now have WFD using HDCP on your QCom device. You can test using a
QCom devellopment device, with the wfd\_client application, connected to
a dongle using test certificates <span id="line-125"
class="anchor"></span><span id="line-126" class="anchor"></span>

#### Device - TZ version {#Device_-_TZ_version}

<span id="line-127" class="anchor"></span>
-   MAKO - 1033 <span id="line-128" class="anchor"></span>
-   Motorola - 2305 <span id="line-129" class="anchor"></span>
-   F3 Optimus - 12132 <span id="line-130" class="anchor"></span>
-   ZTE - 17332 <span id="line-131" class="anchor"></span><span
    id="line-132" class="anchor"></span>

#### Projects {#Projects}

<span id="line-133" class="anchor"></span>
<div>

  ----------------------- ----------------------- -----------------------
  Project                 Marketing               Technical Lead

  <span id="line-134"     Raviv                   Dima
  class="anchor"></span>                          
  [Qualcomm](/CP/PROJECTS                         
  /Qualcomm/HDCP)                                 

  <span id="line-135"     Raviv                   Dima
  class="anchor"></span>                          
  [NVidia](/CP/PROJECTS/N                         
  Vidia/HDCP){.nonexisten                         
  t}                                              

  <span id="line-136"     Raviv                   Ron
  class="anchor"></span>                          
  [Samsung](/CP/PROJECTS/                         
  Samsung/HDCP)                                   

  <span id="line-137"     Raviv                   Ron
  class="anchor"></span>                          
  [HTC](/CP/PROJECTS/HTC/                         
  HDCP)                                           

  <span id="line-138"     Raviv                   Ron
  class="anchor"></span>                          
  [Sharp](/CP/PROJECTS/Sh                         
  arp/HDCP)                                       

  <span id="line-139"     Raviv                   Ron
  class="anchor"></span>                          
  [Sony](/CP/PROJECTS/Son                         
  y/HDCP)                                         

  <span id="line-140"     Raviv                   Ron
  class="anchor"></span>                          
  [Motorola](/CP/PROJECTS                         
  /Motorola/HDCP)                                 
  ----------------------- ----------------------- -----------------------

</div>

<span id="line-141" class="anchor"></span><span id="bottom"
class="anchor"></span>

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
