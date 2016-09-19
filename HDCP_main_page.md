
# HDCP product main page 

## DxHdcp Prerequisites
- ping between Transmitter device and Receiver device should take no
  longer than 4 ms
- Wifi power saving mode should be turned off. WFD disables the power
  saving mode, however QA\_TST needs power saving mode off in wifi config
  file On the device.
- On Qualcomm's platform, please modify `/data/misc/wifi/WCNSS_qcom_cfg.ini` 
  with the following values:

 ```
    gEnableBmps=0 
    gEnableImps=0 
    gDot11Mode=3 
  ```
**Note**: on some devices the location of the wifi configuration file
was changed to: `/system/etc/wifi/WCNSS_qcom_cfg.ini` or `/system/etc/firmware/wlan/qca_cld/ `

## TZ Application

- The TZ application address for HDCP is: 0x88E00000 unless defined otherwise in specific project 
- For Project Specific address, go to the project page: [TZInfra](//github.com/ARMmbed/ta-TZInfra)
- Location of Development guide which contains info for building the TZ app: [DxHDCP Qualcomm Developer Guide]      (https://github.com/ARMmbed/ta-DxHDCP/blob/master/docs/deliverables/ARM%20TrustZone%20Protected%20HDCP%20over%20Qualcomm%20Developer%2   0Guide.docx)

## HDCP Dongles 
- Info about how to change dongle properties can found here: [DONGLES](/master/docs/internal/DONGLES) 

## HDCP debugging
-   For Analyzing HDCP packets through wireshark, please enable HDCP protocol in wireshark.
-   Instructions can be found [here](/ta-DxHDCP/blob/master/README.md#hdcp-traffic-analysis).

## Enabling WFD working with HDCP on Qualcomm Devices 
- To enable HDCP in WFD, on qualcomm devices, there are two files in the
  Qualcomm device that needs to be modified:
   -  In the device, under the path `/system/etc/wfdconfig.xml` there is a
    tag inside Capabilities that is called `ContentProtection`.
    -   It has a parameter **`Valid`** ( on some platforms it is called
        **`HDCPValid`**). It should be set to 1. 
    -   Another parameter called `EncryptAudio` should be set to '1'
        in case Audio should be encrypted. 
    -   Then push the updated `wfdconfig.xml` into `/system/etc` 
- **Note:** For MSM8994 and newest devices exist capability to be a Sink in this case needs to be modified `wfdsinkconfig.xml`
-  Rebuilding WFD module to work and link with DxHdcp library:
    -   in the Qcom source tree root: 
    ```
    mkdir -p vendor/qcom/proprietary/wfd-noship/mm/hdcp/HDCP_API 
    gedit vendor/qcom/proprietary/wfd-noship/Android.mk
    gedit vendor/qcom/proprietary/wfd-noship/mm/ 
    ```
    -That will have the following: 
    
    ```
    ifeq ($(call is-vendor-board-platform,QCOM),true)
    ifneq ($(call is-board-platform,copper),true)
    include $(call all-subdir-makefiles)
    endif
     endif # TARGET_USES_WFD
    ```
    - Copy `libDxHdcp.so` to `vendor/qcom/proprietary/wfd-noship/mm/hdcp/`
    it is needed for linking the wfd library 
    - Copy the DxHdcp header files to `vendor/qcom/proprietary/wfd-noship/mm/hdcp/HDCP_API`
    - **Android L and above**        
    ```
    gedit vendor/qcom/proprietary/wfd-noship/mm/hdcp/Android.mk 
    ```
    -  With the following values:
    
    ```
    LOCAL_PATH := $(call my-dir)
    include $(CLEAR_VARS)
    LOCAL_SRC_FILES := libDxHdcp.so
    LOCAL_MODULE := libDxHdcp
    LOCAL_MODULE_SUFFIX := .so
    LOCAL_MODULE_TAGS := optional
    LOCAL_MODULE_CLASS := SHARED_LIBRARIES
    LOCAL_MULTILIB := 32
    include $(BUILD_PREBUILT)
    ```
    - Build the HDCP prebuilt module:

    ```
    pushd vendor/qcom/proprietary/wfd-noship/mm/hdcp/
    mm -B
    popd
    ```
    
    - **Note:** To make sure that the library has been built properly, you can add a warning in the source file:
    `vendor/qcom/proprietary/wfd/mm/hdcp/common/src/**WFD_HdcpCP.cpp**`
 
    - Look up `CWFD_HdcpCp::WFD_HdcpSessionInit` and add a warning inside `#ifdef WFD_HDCP_ENABLED`.For example:
    ``` 
    #ifdef WFD_HDCP_ENABLED
    ...
    #warning WFD_HdcpSessionInit - HDCP ENABLED
    #else
    #warning WFD_HdcpSessionInit - HDCP DISABLED
    #endif //WFD_HDCP_ENABLED
    ```
   - **Note:** If COMPILE_HDCP_LIB will not set to true automaticlly as usual, 
   that's the root cause in this case and happend for all 8996 projects.
   - Fix: add COMPILE_HDCP_LIB :=true manually.
   ```
    COMPILE_HDCP_LIB := false
    WFD_NOSHIP_HDCP_PATH  := $(LOCAL_PATH)/../../../../wfd-noship/mm/hdcp
    WFD_INTERNAL_LIB_PATH := $(TOP)/vendor/qcom/proprietary/wfd-internal/mm/hdcp/lib
    COMPILE_HDCP_LIB := $(shell if [[ -d $(WFD_NOSHIP_HDCP_PATH) && -d $(WFD_INTERNAL_LIB_PATH) ]] ; then echo true; fi)
    COMPILE_HDCP_LIB :=true
    ```
   - **Rebuild** libwfdhdcpcp:
    ```
    pushd vendor/qcom/proprietary/wfd/mm/hdcp/
    mm -B
    popd
    ```
    
    - **Note:** If `mm` fails due to missing dependencies,
    then try `mma` instead. 
    -   push libwfdhdcpcp that was built from
    `<Qcom source tree root>/out/target/product/<product name>/system/vendor/lib/libwfdhdcpcp.so`
    to `/system/lib` in the device ( on newer builds, the path is `/system/vendor/lib/`) 
    - push libwfdhdcpcp that was built from
    `<Qcom source tree root>/out/target/product/<product name>/system/vendor/lib64/libwfdhdcpcp.so`
    to `/system/lib64` in the device ( on newer builds, the path is `/system/vendor/lib64/`)
    - **Before Android L**

    ```
    gedit vendor/qcom/proprietary/wfd-noship/mm/hdcp/Android.mk 
    ```
    - with the following:
    ```
    LOCAL_PATH := $(call my-dir)
    include $(CLEAR_VARS)
    LOCAL_SRC_FILES := libDxHdcp.so
    LOCAL_MODULE := libDxHdcp
    LOCAL_MODULE_SUFFIX := .so
    LOCAL_MODULE_TAGS := optional
    LOCAL_MODULE_CLASS := SHARED_LIBRARIES
    include $(BUILD_PREBUILT)
    ```
    - in case the tree or libwfdhdcpcp was already built, clean libwfdhdcpcp from `<Qcom source tree root>`:
    ```
     make clean-libwfdhdcpcp
     make libwfdhdcpcp
    ``` 
    - push libwfdhdcpcp that was built from
    `<Qcom source tree root>\out\target\product\<product name>\system\lib\libwfdhdcpcp.so`
    to `/system/lib` in the device ( on newer builds, the path is `/system/vendor/lib/`) 

   - Now WFD can use HDCP on QCom device. 
   - QCom devellopment device can be used for [E2E tests](/ta-DxHDCP/blob/master/docs/internal/HDCP%20End%20to%20End%20testing%20guide.docx) with the wfd_client application, connected to
   a DONGLE using test certificates.

