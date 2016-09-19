#DONGLES

 - **Please note:** 
   - Here you can find all known commands that changes Dongle's properties.
   - All changes possible to do **ONLY** to Cavium dongle.
   - All another Dongles exist in stock now are "Production Devices" and don`t do any changes
   - You must have console access to the dongle (Cavium). For example, you can use [Minicom](https://help.ubuntu.com/community/Minicom).
   - You need to know how to connect to the dongle with [u-boot command mode](http://www.stlinux.com/u-boot/using).
   - When using setenv command DO NOT use '='
   - More info can found in [HDCP End to End testing guide](/ta-DxHDCP/docs/internal/HDCP End to End testing guide.docx)
   
## Changing to Test Keys:

 - `setenv HDCP_FACSIMILE_KEY 1`
 - `setenv ENABLE_SW_CRYPTO 1`
 - `saveenv`
 - `reset`
  
## Changing to Production Keys:

 - `setenv HDCP_FACSIMILE_KEY 0`
 - `setenv ENABLE_SW_CRYPTO 0`
 - `saveenv`
 - `reset`
  
## To keep HDCP socket open after AKE:

 - `setenv CLOSE_HDCP_SOCKET 0`
 - `saveenv`
 - `reset`

## To Change LOGGING level:

 - `setenv SYSLOG_LEVEL=X`
   - X = 3 (minimal), 6 (maximum)
 - `saveenv`
 - `reset`
 
## Troubleshoot:

 - In case the dongle is not working (even after successful flash), try to check the following:
   - if MODE is not WFD in the printenv list do:
   - `setenv MODE WFD`
   - `saveenv`
   - `reset`
   
## Additional info:

 - `sete` is short form for `setenv`.
