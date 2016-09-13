<div id="header">

<div>

Search:

</div>

<div id="logo">

[![MoinMoin Logo](/moin_static194/common/moinmoin.png)](/FrontPage)

</div>

<span id="pagelocation"><span class="pagepath">[CP](/CP)<span class="sep">/</span>[PS](/CP/PS)<span class="sep">/</span>[DEVICES](/CP/PS/DEVICES)<span class="sep">/</span>[QC\_Jtag\_Flash](/CP/PS/DEVICES/QC_Jtag_Flash)</span><span class="sep">/</span>[General](/CP/PS/DEVICES/QC_Jtag_Flash/General?action=fullsearch&value=linkto%3A%22CP%2FPS%2FDEVICES%2FQC_Jtag_Flash%2FGeneral%22&context=180 "Click to do a full-text search for this title"){.backlink}</span> {#locationline}
===========================================================================================================================================================================================================================================================================================================================================================================================================================================================================

-   [RecentChanges](/RecentChanges)
-   [FindPage](/FindPage)
-   [HelpContents](/HelpContents)
-   [General](/CP/PS/DEVICES/QC_Jtag_Flash/General)

<div id="pageline">

------------------------------------------------------------------------

</div>

</div>

<div id="page" lang="en" dir="ltr">

<div id="content" dir="ltr" lang="en">

<span id="top" class="anchor"></span> <span id="line-1"
class="anchor"></span><span id="line-2" class="anchor"></span><span
id="line-3" class="anchor"></span><span id="line-4"
class="anchor"></span><span id="line-5" class="anchor"></span><span
id="line-6" class="anchor"></span>
This Page Describes How to Flash Qualcomm Fluid or MDP <span id="line-7"
class="anchor"></span>

QSEE\_Jtag\_Flash {#QSEE_Jtag_Flash}
=================

<span id="line-8" class="anchor"></span><span id="line-9"
class="anchor"></span>

<div class="table-of-contents">

Contents

1.  [QSEE\_Jtag\_Flash](#QSEE_Jtag_Flash)
    1.  [Before Starting Please note:](#Before_Starting_Please_note:)
    2.  [Download and prepare directory for
        flashing:](#Download_and_prepare_directory_for_flashing:)
    3.  [Prepare the device to flash:](#Prepare_the_device_to_flash:)
    4.  [Hardware Tools:](#Hardware_Tools:)

</div>

<span id="line-10" class="anchor"></span><span id="line-11"
class="anchor"></span>

Before Starting Please note: {#Before_Starting_Please_note:}
----------------------------

<span id="line-12" class="anchor"></span><span id="line-13"
class="anchor"></span>
-   The Flashing is on Windows <span id="line-14" class="anchor"></span>
-   Software: You need the following: <span id="line-15"
    class="anchor"></span>
    -   OUT directory from Android Compilation <span id="line-16"
        class="anchor"></span>
    -   Download all HK and HY directories from Qualcomm Docs&Downloads
        <span id="line-17" class="anchor"></span>
    -   Trace32 installed on your computer (with specific definitions) -
        see [here](http://172.16.7.200/CP/PS/TOOLS/TRACE32){.http} <span
        id="line-18" class="anchor"></span>
    -   Python 2.7 (Wasn't tested with later version) <span id="line-19"
        class="anchor"></span>
    -   Note: put python and fastboot apps in windows PATH,
        <http://geekswithblogs.net/renso/archive/2009/10/21/how-to-set-the-windows-path-in-windows-7.aspx>
        <span id="line-20" class="anchor"></span>
-   Hardware: You need the following: <span id="line-21"
    class="anchor"></span>
    -   Lauterbach (+power adapter, and USB cable) <span id="line-22"
        class="anchor"></span>
    -   MDP or SURF <span id="line-23" class="anchor"></span>
    -   Debug Board if flashing an MDP (+power adapter and USB cable)
        <span id="line-24" class="anchor"></span><span id="line-25"
        class="anchor"></span><span id="line-26" class="anchor"></span>

Download and prepare directory for flashing: {#Download_and_prepare_directory_for_flashing:}
--------------------------------------------

<span id="line-27" class="anchor"></span>
-   Go to Docs&Downloads site and choose the Platform and build number
    that you want to flash <span id="line-28" class="anchor"></span>

    -   Download all **HK** zip files (except for "common", only HY zip
        file should be downloaded) <span id="line-29"
        class="anchor"></span>
    -   Download **HY** zip files with the "boot\_images" and
        "common" folders. (common is the directory inside the zip file,
        most of the time, the zip that located in the root list of the
        files on the site is the common zip ) <span id="line-30"
        class="anchor"></span>
    -   NOTE: All HK and HY zip files located inside the directories
        <span id="line-31" class="anchor"></span>

![Docs&Downlaods.png](/CP/PS/DEVICES/QC_Jtag_Flash/General?action=AttachFile&do=get&target=Docs%26Downlaods.png "Docs&Downlaods.png"){.attachment}
<span id="line-32" class="anchor"></span>

-   Create a new directory ( it doesn't matter the name of it, in this
    guide it will be called &lt;ROOT&gt; ) <span id="line-33"
    class="anchor"></span>
-   Extract and copy common HY to &lt;ROOT&gt; directory <span
    id="line-34" class="anchor"></span>
-   Extrat and copy boot\_imagres HY to &lt;ROOT&gt; directory <span
    id="line-35" class="anchor"></span>
-   Extract the HK archives (except to boot\_images and common) to the
    &lt;ROOT&gt; directory <span id="line-36" class="anchor"></span>
-   NOTE: You may miss some directories for example "modem\_proc" that
    wont be in the docs&downloads <span id="line-37"
    class="anchor"></span>

![FilesList.png](/CP/PS/DEVICES/QC_Jtag_Flash/General?action=AttachFile&do=get&target=FilesList.png "FilesList.png"){.attachment}
<span id="line-38" class="anchor"></span>

-   After extracting you will have LINUX folder, inside this directory
    you should have "android\\vendor" directory <span id="line-39"
    class="anchor"></span>
    -   You must copy the "out" directory (output from android
        tree compilation) to the LINUX\\android\\ directory. <span
        id="line-40" class="anchor"></span>
    -   Make sure the out directory compiled with the correct platform
        name and build number. <span id="line-41" class="anchor"></span>
    -   Note: while copy the out directory from linux to windows you may
        have overwrite message, if you do, press overwrite all. <span
        id="line-42" class="anchor"></span>
-   Run the python script ‘update\_common\_info.py’ from common/build.
    This is what you should see at the end of the script: <span
    id="line-43" class="anchor"></span>

![python.png](/CP/PS/DEVICES/QC_Jtag_Flash/General?action=AttachFile&do=get&target=python.png "python.png"){.attachment}
<span id="line-44" class="anchor"></span>

-   Copy the "boot\_images" folder from the HK archive to the
    &lt;ROOT&gt; directory, and delete/move/rename the existing one (HY)
    and all its content. <span id="line-45" class="anchor"></span><span
    id="line-46" class="anchor"></span>

Prepare the device to flash: {#Prepare_the_device_to_flash:}
----------------------------

<span id="line-47" class="anchor"></span>
-   See "Hardware Tools" section below to see the Debug board and
    Lauterbach pictures and connections. <span id="line-48"
    class="anchor"></span>
-   MDP only: Connect the MDP to the Debug board <span id="line-49"
    class="anchor"></span>
-   Connect the Lauterbach and the Debug Board/SURF to the power <span
    id="line-50" class="anchor"></span>
-   Connect the Lauterbach to the PC (with USB) <span id="line-51"
    class="anchor"></span>
-   Optional: Connect the Debug Board/SURF to the PC (with USB) <span
    id="line-52" class="anchor"></span>
-   Start fastboot in the MDP/SURF: (keep volume down button during
    power up cycle) <span id="line-53" class="anchor"></span>
    -   Disconnect usb cable and power from the MDP/SURF <span
        id="line-54" class="anchor"></span>
    -   Connect the Power cable <span id="line-55"
        class="anchor"></span>
    -   keep volume down button (keep pressing) <span id="line-56"
        class="anchor"></span>
    -   Connect the USB cable <span id="line-57" class="anchor"></span>
    -   The LCD will stuck on the penguin picture (see picture below to
        see how the connections should look like) <span id="line-58"
        class="anchor"></span><span id="line-59"
        class="anchor"></span><span id="line-60" class="anchor"></span>

Hardware Tools: {#Hardware_Tools:}
---------------

<span id="line-61" class="anchor"></span>
Note: The pictures below is for 8960 but other platforms look similar.
<span id="line-62" class="anchor"></span><span id="line-63"
class="anchor"></span>

![Lauterbach.png](/CP/PS/DEVICES/QC_Jtag_Flash/General?action=AttachFile&do=get&target=Lauterbach.png "Lauterbach.png"){.attachment}
<span id="line-64"
class="anchor"></span>![DebugBoard.png](/CP/PS/DEVICES/QC_Jtag_Flash/General?action=AttachFile&do=get&target=DebugBoard.png "DebugBoard.png"){.attachment}
<span id="line-65"
class="anchor"></span>![Final.png](/CP/PS/DEVICES/QC_Jtag_Flash/General?action=AttachFile&do=get&target=Final.png "Final.png"){.attachment}
<span id="line-66" class="anchor"></span><span id="bottom"
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
