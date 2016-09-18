
# Downloading,Building And Flashing QC Android devices

## Contents

- Downloading,Building And Flashing QC Android devices
    -  Downloading QC Images
        -  Downloading the QC proprietary code
        -  Downloading Open Source QC Code
    -  Building the QC images
        -  Preparations
        -  Building
    -  Flashing QC images

 **Note:** All of the steps below should be done on a Linux Machine( on old
   versions, Ubuntu 10.04 is recommended, on Kitkat versions, Ubuntu 12.04
   can be used) 

## Downloading QC Images
The QC image is consisted of two major parts: 
-   QC proprietary code 
-   QC open source code, including the Android Source Tree

## Downloading the QC proprietary code

-  QC maintains external branches for customers. These branches can be
   downloaded from https://chipcode.qti.qualcomm.com
   - Login credentials must be created.
-  In the site, select the desired branch to be downloaded In the branch
   page, select the link with the precompiled binaries (usually containing
   pre-compiled\_device or amss\_device )
   downloading from this branches requires git in the selected link, there
   will be a reference for the git url to download for e.g.
   https://chipcode.qti.qualcomm.com/home/git/msm8974-la-4-0-4_amss_premier_oem.git
-  Download the git repository:
    -   for first download from this branch, use git clone: 
    ```
    git clone <the_found_git_repository>
    ```
    
    **Note: If this git repo was mirrored onto AOSP, then use the aosp
    git url to download e.g.: 
    ```
    git clone git://mng-it1/aosp/<git-repository-name>
    ```
-   **Note:** List of mirrored repo can see on: \\qnap\aosp
    **E.g.:** 

    ``` 
    git clone git://mng-it1/aosp/msm8974-la-4-0-4_amss_premier_oem.git
    ```
    Already downloaded:

    ``` 
    cd <repository folder>
    git fetch
    ``` 
-  Select desired tag : 

    ```
    cd <repository folder>
    git checkout <tag>
    ``` 
    
    **Note:** you may use `git tag` in order to see the list of possible
    tags
## Downloading Open Source QC Code 
   For Downloading the QCT aosp source code, one will need repo, as defined
   in http://source.android.com/source/downloading.html
   Verify you have reference aosp, for faster downloading, if not, do the
   following:
   
   ```
    sudo mount filesrv:/vol/vol2/aosp  /aosp
   ```
   
 - In repository folder open the file `contents.xml` and search
   for `build` node with `<name>apps</name>`. 
 - In this build node there should be a `build_id` parameter.
 - Remember this `build_id`!!!
 - In some (newer) versions the `build_id` tag would be empty in `contents.xml`. 
 - In that case, open the `about.html` (located in the same place as
   `contents.xml` and look in the "Build Components" table for
   the label of the LINUX component - that label should be used instead of
   `build_id`
-  Open https://www.codeaurora.org/xwiki/bin/QAEP
-  In this page select the desired branch ( Usually it is release branch ) 
-  Search for the `build_id` you found in the
   `contents.xml` (or `about.html`, as detailed
   above (sometimes last digit of the `build_id` is omitted
   in this page).
-  The .xml conatining this `build_id` is the manifest needed for
   downloading the source code

  ```
    mkdir <Android root>
    cd <Android root>
    repo init -u git://codeaurora.org/platform/manifest.git -b <branch_name (usually release)> -m <manifest>.xml --reference=/aosp/codeaurora-mirror
    repo sync
    ```
## Building the QC images 

### preparations
The QC proprietary code should be merged into the QC open source code,
by copying 

 ```
    cp -r <repository folder>/LINUX/android/vendor/qcom/proprietary <Android root>/vendor/qcom
 ```
 
*** Recommendations for **WFD+HDCP**
-  It is recommended to build the image with support for **HDCP**, as
    described in /master/docs/internal/HDCP_main_page

### Building

 ```
    cd <Android root>
    source build/envsetup.sh
    choosecombo 1 <target> eng
    make
 ```
 
-  **Note:** Instead of using `choosecombo` you may need to execute `lunch`
   and choose the platform for which you would like to build.

-  Target can be one of the following:
   -  `msm8974` for TZ2.x 
   -  `msm8994` for TZ2.x
   -  `msm8996` for TZ4.x)

 -  **Note:** Using `-j` option for `make` may result in compilation error, 
    due to dependencies problem in Qualcomm's proprietary modules.

 ## Flashing QC images
-  The safest way for flashing an image, should be done through JTag, as described in
[/master/docs/internal/Flashing msm8974 by QFIL.md] or [/master/docs/internal/MSM8996 downloading and burning]
However, if the partition table hasn't changed, flashing by fastboot can
be done as well: 

 ```
    adb reboot bootloader
    cd <repository folder>/common/build
    sudo python ./fastboot_complete.py <Android root>
 ```
- The script can use a default parameter, if the out path is not
  set, and if the out folder from **Android root** will be copied to
  **repository folder/LINUX/android** 
- The safest thing to do is (especially if the Android images are not
  flashed), is to copy the out folder from **Android root** to
  **repository folder/LINUX/android**
- It's generally better to use the tree with the built images for burning
- Once flashing completes, as shown in terminal, press ctrl c and reboot the device
- **Note:** Some images will require enabling battery charging after flashing:

 ```
    adb root
    adb shell setprop persist.usb.chgdisabled 0
    adb sync
 ```
 - **Note:** on 8084 and later devices, after first-time burning, need to
   cleanup RPMB partition:
 ```
    qseecom_sample_client -v sampleapp 14 1
    * select 1 (Provision Test Key)
    qseecom_sample_client -v sampleapp 15 1
    * select y (yes for proceeding in RPMB partition erasing)
 ```    
    * Reboot device
    * After reboot, writing to sfs should succeed ( if not, delete /persist/data/* and then retry)
