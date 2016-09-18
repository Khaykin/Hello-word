<div id="header">

<div>

Search:

</div>

<div id="logo">

[![MoinMoin Logo](/moin_static194/common/moinmoin.png)](/FrontPage)

</div>

<span id="pagelocation"><span class="pagepath">[CP](/CP)<span class="sep">/</span>[PS](/CP/PS)<span class="sep">/</span>[DEVICES](/CP/PS/DEVICES)</span><span class="sep">/</span>[QC\_Build\_And\_Flash](/CP/PS/DEVICES/QC_Build_And_Flash?action=fullsearch&value=linkto%3A%22CP%2FPS%2FDEVICES%2FQC_Build_And_Flash%22&context=180 "Click to do a full-text search for this title"){.backlink}</span> {#locationline}
========================================================================================================================================================================================================================================================================================================================================================================================================

-   [RecentChanges](/RecentChanges)
-   [FindPage](/FindPage)
-   [HelpContents](/HelpContents)
-   [QC\_Build\_And\_Flash](/CP/PS/DEVICES/QC_Build_And_Flash)

<div id="pageline">

------------------------------------------------------------------------

</div>

</div>

<div id="page" lang="en" dir="ltr">

<div id="content" dir="ltr" lang="en">

<span id="top" class="anchor"></span> <span id="line-1"
class="anchor"></span>

Downloading,Building And Flashing QC Android devices {#Downloading.2CBuilding_And_Flashing_QC_Android_devices}
====================================================

<span id="line-2" class="anchor"></span>

<div class="table-of-contents">

Contents

1.  [Downloading,Building And Flashing QC Android
    devices](#Downloading.2CBuilding_And_Flashing_QC_Android_devices)
    1.  [Downloading QC Images](#Downloading_QC_Images)
        1.  [Downloading the QC proprietary
            code](#Downloading_the_QC_proprietary_code)
        2.  [Downloading Open Source QC
            Code](#Downloading_Open_Source_QC_Code)

    2.  [Building the QC images](#Building_the_QC_images)
        1.  [preparations](#preparations)
        2.  [Building](#Building)

    3.  [Flashing QC images](#Flashing_QC_images)

</div>

<span id="line-3" class="anchor"></span><span id="line-4"
class="anchor"></span>
\
All of the steps below should be done on a Linux Machine( on old
versions, Ubuntu 10.04 is recommended, on Kitkat versions, Ubuntu 12.04
can be used) <span id="line-5" class="anchor"></span><span id="line-6"
class="anchor"></span>

Downloading QC Images {#Downloading_QC_Images}
---------------------

<span id="line-7" class="anchor"></span>
The QC image is consisted of two major parts: <span id="line-8"
class="anchor"></span><span id="line-9" class="anchor"></span>

-   QC proprietary code <span id="line-10" class="anchor"></span>
-   QC open source code, including the Android Source Tree <span
    id="line-11" class="anchor"></span><span id="line-12"
    class="anchor"></span>

### Downloading the QC proprietary code {#Downloading_the_QC_proprietary_code}

<span id="line-13" class="anchor"></span>
QC maintains external branches for customers. These branches can be
downloaded from <https://chipcode.qti.qualcomm.com>\
login credentials: <span id="line-14" class="anchor"></span><span
id="line-15" class="anchor"></span>

Username: <kobe.shapira@discretix.com> <span id="line-16"
class="anchor"></span><span id="line-17" class="anchor"></span>

Password: Discretix2011 <span id="line-18" class="anchor"></span><span
id="line-19" class="anchor"></span>

In the site, select the desired branch to be downloaded In the branch
page, select the link with the precompiled binaries (usually containing
pre-compiled\_device or amss\_device ) <span id="line-20"
class="anchor"></span><span id="line-21" class="anchor"></span>

downloading from this branches requires git in the selected link, there
will be a reference for the git url to download ( e.g.
<https://chipcode.qti.qualcomm.com/home/git/msm8974-la-4-0-4_amss_premier_oem.git>
) <span id="line-22" class="anchor"></span><span id="line-23"
class="anchor"></span>

1.  download the git repository:\
    for first download from this branch, use git clone: <span
    id="line-24" class="anchor"></span><span id="line-25"
    class="anchor"></span><span id="line-26" class="anchor"></span>

         git clone <the_found_git_repository>

    <span id="line-27" class="anchor"></span>

    **Note: If this git repo was mirrored onto AOSP, then use the aosp
    git url to download. I.e.:** <span id="line-28"
    class="anchor"></span><span id="line-29" class="anchor"></span><span
    id="line-30" class="anchor"></span>

         git clone git://mng-it1/aosp/<git-repository-name>

    <span id="line-31" class="anchor"></span>

    **E.g.:** <span id="line-32" class="anchor"></span>

    -   Note: List of mirrored repo can see on: \\\\qnap\\aosp <span
        id="line-33" class="anchor"></span>

    <span id="line-34" class="anchor"></span><span id="line-35"
    class="anchor"></span>

         git clone git://mng-it1/aosp/msm8974-la-4-0-4_amss_premier_oem.git

    <span id="line-36" class="anchor"></span>in case this branch was
    already downloaded: <span id="line-37" class="anchor"></span><span
    id="line-38" class="anchor"></span><span id="line-39"
    class="anchor"></span><span id="line-40" class="anchor"></span>

         cd <repository folder>
         git fetch

    <span id="line-41" class="anchor"></span><span id="line-42"
    class="anchor"></span>

2.  select desired tag : <span id="line-43" class="anchor"></span><span
    id="line-44" class="anchor"></span><span id="line-45"
    class="anchor"></span><span id="line-46" class="anchor"></span>

         cd <repository folder>
         git checkout <tag>

    <span id="line-47" class="anchor"></span>

    **Note: you may use `git tag` in order to see the list of possible
    tags** <span id="line-48" class="anchor"></span><span id="line-49"
    class="anchor"></span>

### Downloading Open Source QC Code {#Downloading_Open_Source_QC_Code}

<span id="line-50" class="anchor"></span>
For Downloading the QCT aosp source code, one will need repo, as defined
in <http://source.android.com/source/downloading.html>\
Verify you have reference aosp, for faster downloading, if not, do the
following: <span id="line-51" class="anchor"></span><span id="line-52"
class="anchor"></span>

<span id="line-53" class="anchor"></span><span id="line-54"
class="anchor"></span>

    sudo mount filesrv:/vol/vol2/aosp  /aosp

<span id="line-55" class="anchor"></span>
In the &lt;repository folder&gt; open the file contents.xml and search
for `<build>`{.backtick} node with `<name>apps</name>`{.backtick}. In
this build node there should be a `<build_id>`{.backtick} parameter.
remember this `build_id`{.backtick}\
![{i}](/moin_static194/modernized/img/icon-info.png "{i}"){width="16"
height="16"} In some (newer) versions the `<build_id>`{.backtick} tag
would be empty in `contents.xml`{.backtick}. In that case, open the
`about.html`{.backtick} (located in the same place as
`contents.xml`{.backtick}) and look in the "Build Components" table for
the label of the LINUX component - that label should be used instead of
`build_id`{.backtick}. <span id="line-56" class="anchor"></span><span
id="line-57" class="anchor"></span>

-   Open <https://www.codeaurora.org/xwiki/bin/QAEP/> <span id="line-58"
    class="anchor"></span>
-   In this page select the desired branch ( Usually it is release
    branch ) <span id="line-59" class="anchor"></span>
-   Search for the `build_id`{.backtick} you found in the
    `contents.xml`{.backtick} (or `about.html`{.backtick}), as detailed
    above (sometimes last digit of the `build_id`{.backtick} is omitted
    in this page). <span id="line-60" class="anchor"></span>
-   The .xml conatining this build\_id is the manifest needed for
    downloading the source code <span id="line-61"
    class="anchor"></span><span id="line-62" class="anchor"></span>

<span id="line-63" class="anchor"></span><span id="line-64"
class="anchor"></span><span id="line-65" class="anchor"></span><span
id="line-66" class="anchor"></span><span id="line-67"
class="anchor"></span>

    mkdir <Android root>
    cd <Android root>
    repo init -u git://codeaurora.org/platform/manifest.git -b <branch_name (usually release)> -m <manifest>.xml --reference=/aosp/codeaurora-mirror
    repo sync

<span id="line-68" class="anchor"></span>

Building the QC images {#Building_the_QC_images}
----------------------

<span id="line-69" class="anchor"></span>

### preparations

<span id="line-70" class="anchor"></span>
The QC proprietary code should be merged into the QC open source code,
by copying <span id="line-71" class="anchor"></span><span id="line-72"
class="anchor"></span>

<span id="line-73" class="anchor"></span><span id="line-74"
class="anchor"></span>

    cp -r <repository folder>/LINUX/android/vendor/qcom/proprietary <Android root>/vendor/qcom

<span id="line-75" class="anchor"></span>
**Recommendations for <span class="u">CPRM</span> and** **<span
class="u">WFD+HDCP</span>** **support:** <span id="line-76"
class="anchor"></span><span id="line-77" class="anchor"></span>

1.  It is recommended to build the image with support for **HDCP**, as
    described in [CP/PRODUCTS/HDCP](/CP/PRODUCTS/HDCP) <span
    id="line-78" class="anchor"></span><span id="line-79"
    class="anchor"></span>
2.  It is recommended to apply **CPRM** kernel patches, as defined in
    the CPRM developer's guide ( for CPRM users ) <span id="line-80"
    class="anchor"></span><span id="line-81" class="anchor"></span>

### Building {#Building}

<span id="line-82" class="anchor"></span>
<span id="line-83" class="anchor"></span><span id="line-84"
class="anchor"></span><span id="line-85" class="anchor"></span><span
id="line-86" class="anchor"></span><span id="line-87"
class="anchor"></span>

    cd <Android root>
    source build/envsetup.sh
    choosecombo 1 <target> eng
    make

<span id="line-88" class="anchor"></span>
**Note: Instead of using `choosecombo` you may need to execute `lunch`
and choose the platform for which you would like to build.** <span
id="line-89" class="anchor"></span><span id="line-90"
class="anchor"></span>

![{i}](/moin_static194/modernized/img/icon-info.png "{i}"){width="16"
height="16"} `<target>`{.backtick} can be one of the following:
`msm8974`{.backtick}(for TZ2.0), `apq8084`{.backtick}(for TZ2.4),
`msm8960`{.backtick}(for TZ1.4) <span id="line-91"
class="anchor"></span><span id="line-92" class="anchor"></span>

![{i}](/moin_static194/modernized/img/icon-info.png "{i}"){width="16"
height="16"} Using "`-j`{.backtick}" option for `make`{.backtick} may
result in compilation error, due to dependencies problem in Qualcomm's
proprietary modules. <span id="line-93" class="anchor"></span><span
id="line-94" class="anchor"></span>

Flashing QC images {#Flashing_QC_images}
------------------

<span id="line-95" class="anchor"></span>
The safest way for flashing an image, should be done through JTag, as
described in
[CP/PS/DEVICES/QC\_Jtag\_Flash](/CP/PS/DEVICES/QC_Jtag_Flash)\
However, if the partition table hasn't changed, flashin by fastboot can
be done as well: <span id="line-96" class="anchor"></span><span
id="line-97" class="anchor"></span>

<span id="line-98" class="anchor"></span><span id="line-99"
class="anchor"></span><span id="line-100" class="anchor"></span><span
id="line-101" class="anchor"></span>

    adb reboot bootloader
    cd <repository folder>/common/build
    sudo python ./fastboot_complete.py <Android root>

<span id="line-102" class="anchor"></span>
![{i}](/moin_static194/modernized/img/icon-info.png "{i}"){width="16"
height="16"} `<repository folder>`{.backtick} is the Chipcode git
repository for the `pre-compiled_device`{.backtick} release image. <span
id="line-103" class="anchor"></span><span id="line-104"
class="anchor"></span>

\
**Note**: the script can use a default parameter, if the out path is not
set, and if the out folder from &lt;Android root&gt; will be copied to
&lt;repository folder&gt;/LINUX/android .\
The safest thing to do is (especially if the Android images are not
flashed), is to copy the out folder from &lt;Android root&gt; to
&lt;repository folder&gt;/LINUX/android\
It's generally better to use the tree with the built images for burning
(normally it's the smaller one from the two we `git clone`-ed).\
For example:\
`/home/rone/dev/QCT/8960_LA2.32/discretix-technologies-ltd-_msm8960-la-2-32_amss_device/LINUX/android`
<span id="line-105" class="anchor"></span><span id="line-106"
class="anchor"></span>

\
once flashing completes, as shown in terminal, press ctrl c\
reboot the device\
\
Note: some images will require enabling battery charging after flashing:
<span id="line-107" class="anchor"></span><span id="line-108"
class="anchor"></span>

<span id="line-109" class="anchor"></span><span id="line-110"
class="anchor"></span><span id="line-111" class="anchor"></span><span
id="line-112" class="anchor"></span>

    adb root
    adb shell setprop persist.usb.chgdisabled 0
    adb sync

<span id="line-113" class="anchor"></span>
Note: on 8084 and later devices, after first-time burning, need to
cleanup RPMB partition: <span id="line-114" class="anchor"></span><span
id="line-115" class="anchor"></span>

<span id="line-116" class="anchor"></span><span id="line-117"
class="anchor"></span><span id="line-118" class="anchor"></span><span
id="line-119" class="anchor"></span><span id="line-120"
class="anchor"></span><span id="line-121" class="anchor"></span><span
id="line-122" class="anchor"></span>

    qseecom_sample_client -v sampleapp 14 1
    * select 1 (Provision Test Key)
    qseecom_sample_client -v sampleapp 15 1
    * select y (yes for proceeding in RPMB partition erasing)
    * Reboot device
    * After reboot, writing to sfs should succeed ( if not, delete /persist/data/* and then retry)

<span id="line-123" class="anchor"></span><span id="bottom"
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
