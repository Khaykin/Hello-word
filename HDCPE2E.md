HDCP

E2E Tests

Testing guide

Version 1.2

Last Updated: July, 2016

<span id="O_15373" class="anchor"></span>**Confidential Proprietary
Notice **

This document is CONFIDENTIAL and any use by you is subject to the terms
of the agreement between you and ARM^®^ or the terms of the agreement
between you and the party authorised by ARM^®^ to disclose this document
to you.

This document is protected by copyright and other related rights and the
practice or implementation of the information contained in this document
may be protected by one or more patents or pending patent applications.
No part of this document may be reproduced in any form by any means
without the express prior written permission of ARM. **No license,
express or implied, by estoppel or otherwise to any intellectual
property rights is granted by this document unless specifically
stated.**

Your access to the information in this document is conditional upon your
acceptance that you will not use or permit others to use the
information: (i) for the purposes of determining whether implementations
infringe any third party patents; (ii) for developing technology or
products which avoid any of ARM’s intellectual property; or (iii) as a
reference for modifying existing patents or patent applications or
creating any continuation, continuation in part, or extension of
existing patents or patent applications; or (iv) for generating data for
publication or disclosure to third parties, which compares the
performance or functionality of the ARM^®^ technology described in this
document with any other products created by you or a third party,
without obtaining ARM’s prior written consent.

THIS DOCUMENT IS PROVIDED "AS IS". ARM^®^ PROVIDES NO REPRESENTATIONS
AND NO WARRANTIES, EXPRESS, IMPLIED OR STATUTORY, INCLUDING, WITHOUT
LIMITATION, THE IMPLIED WARRANTIES OF MERCHANTABILITY, SATISFACTORY
QUALITY, NON-INFRINGEMENT OR FITNESS FOR A PARTICULAR PURPOSE WITH
RESPECT TO THE DOCUMENT. For the avoidance of doubt, ARM^®^ makes no
representation with respect to, and has undertaken no analysis to
identify or understand the scope and content of, third party patents,
copyrights, trade secrets, or other rights. 

This document may include technical inaccuracies or typographical
errors.

TO THE EXTENT NOT PROHIBITED BY LAW, IN NO EVENT WILL ARM^®^ BE LIABLE
FOR ANY DAMAGES, INCLUDING WITHOUT LIMITATION ANY DIRECT, INDIRECT,
SPECIAL, INCIDENTAL, PUNITIVE, OR CONSEQUENTIAL DAMAGES, HOWEVER CAUSED
AND REGARDLESS OF THE THEORY OF LIABILITY, ARISING OUT OF ANY USE OF
THIS DOCUMENT, EVEN IF ARM^®^ HAS BEEN ADVISED OF THE POSSIBILITY OF
SUCH DAMAGES.

This document consists solely of commercial items. You shall be
responsible for ensuring that any use, duplication or disclosure of this
document complies fully with any relevant export laws and regulations to
assure that this document or any portion thereof is not exported,
directly or indirectly, in violation of such export laws. Use of the
word "partner" in reference to ARM’s customers is not intended to create
or refer to any partnership relationship with any other company. ARM^®^
may make changes to this document at any time and without notice.

If any of the provisions contained in these terms conflict with any of
the provisions of any click through or signed written agreement covering
this document with ARM, then the click through or signed written
agreement prevails over and supersedes the conflicting provisions of
these terms. This document may be translated into other languages for
convenience, and you agree that if there is any conflict between the
English version of this document and any translation, the terms of the
English version of the Agreement shall prevail.

Words and logos marked with ^®^ or ™ are registered trademarks or
trademarks of ARM^®^ Limited or its affiliates in the EU and/or
elsewhere. All rights reserved.  Other brands and names mentioned in
this document may be the trademarks of their respective owners. Please
follow ARM’s trademark usage guidelines at
[*http://www.arm.com/about/trademark-usage-guidelines.php*](http://www.arm.com/about/trademark-usage-guidelines.php).

Copyright © 2015, ARM^®^ Limited or its affiliates. All rights reserved.

ARM^®^ Technologies Israel Ltd. Company 513018770 registered in Israel.

Intergamma House, Kfar Netter, Israel.

<span id="O_218" class="anchor"></span>Internal Revision History

  Rev   Date          Author            Description
  ----- ------------- ----------------- -------------------
  1.0   06/Jul/2016   Khaykin Igor      Document creation
  1.1   19/Jul/2016   Dmitry Grinberg   General fixes
  1.2   20/Jul/2016   Khaykin Igor      General fixes

<span id="O_15395" class="anchor"></span>

  -- -- --
        
        
  -- -- --

<span id="O_1989" class="anchor"></span>Contents

1 Introduction 8

1.1 Intended Audience 8

1.2 Referenced Documents 8

1.3 Terms and Abbreviations 8

1.4 Preliminary actions 9

1.5 Preparation to testing 9

2 Sink side devices 11

2.1 Stock of Sink devices 11

2.2 Setup of Sink devices 11

3 Source Side devices 15

3.1 MediaTek 15

3.2 Qualcomm 17

3.3 Windows devices 19

4 Test cases - Source side 22

4.1 Connection between Dongle & DUT (test keys) 22

4.2 Connection between Dongle & DUT (production keys) 23

4.3 Reconnection between dongle & DUT (1) 24

4.4 Reconnection between dongle & DUT(2) 25

4.5 Behavior of HDCP connection after update version (with no stored km)
26

4.6 Behavior of HDCP connection after update version (with stored km) 27

4.7 Behavior of HDCP during connection/disconnection 28

4.8 Behavior of HDCP connection with TZ app test keys via HDMI AVR
receiver 29

4.9 Behavior of multiple HDCP connection with TZ app production keys via
AVR receiver 30

4.10 Behavior of HDCP during plural of connection/disconnection 31

5 Test cases - Sink side 32

5.1 Connection between Source device & DUT 32

5.2 Reconnection DUT and Source devices after valid disconnection 32

5.3 Reconnection DUT and Source devices after non-valid disconnection 33

5.4 Behavior of HDCP connection after update version (with stored km) 34

5.5 Behavior of HDCP connection after update version (with no stored km)
35

6 Trobleshooting 36

List of Figures

**No table of figures entries found.**

List of Tables

Table 1: Referenced Documents 9

Table 2: Glossary 9

Table 3: 3^rd^ party devices in stock 12

<span id="O_205" class="anchor"><span id="_Toc456790859" class="anchor"></span></span>Introduction
==================================================================================================

1.  This document explains how to configure and perform E2E tests
    against 3rd party devices.

2.  The purpose of the tests to check interoperability of HDCP & 3rd
    party devices, shown by display mirroring and followed by HDCP
    authentication (can be checked in logs).

3.  If this is your first time, please read entire document so you may
    utilize the tests to its fullest.

<span id="O_513" class="anchor"><span id="_Toc456790860" class="anchor"></span></span>Intended Audience 
--------------------------------------------------------------------------------------------------------

1.  This document is written to explain for HDCP developers and QA
    testers, who are familiar with current HDCP design, in order to
    perform required HDCP E2E tests.

<span id="O_514" class="anchor"><span id="_Referenced_Documents" class="anchor"><span id="_Toc456790861" class="anchor"></span></span></span>Referenced Documents
-----------------------------------------------------------------------------------------------------------------------------------------------------------------

<span id="_Toc456536728" class="anchor"></span>Table 1: Referenced
Documents

  --------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------
  Ref                                Name
  ---------------------------------- ---------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------
  HDCP Developer guide               <http://master/RnD/Products/Forms/AllItems.aspx?RootFolder=%2fRnD%2fProducts%2fCP%2fLink%20Protection%2fHDCP%2fSW%20Documents%2fDeliverables&FolderCTID=0x0120008C20BA6ADE051A459D53F6D037ED0A39&View=%7b52657E07-5F39-40CC-AC44-3C9578ACA27F%7d>
                                     
  (is platform dependent document)   

  HDCP testing guide                 <http://master/RnD/Products/CP/Link%20Protection/HDCP/QA%20Documents/Internal/BUILDING%20HDCP%20QA%20PACKAGE.docx>

  Wiki Dongle setup                  <http://172.16.7.200/CP/PRODUCTS/HDCP/DONGLES>

  Wiki Using minicom Guide           <http://172.16.7.200/CP/PS/DEVICES/Using_Minicom>

  Sources for using Minicom          <http://processors.wiki.ti.com/index.php/Setting_up_Minicom_in_Ubuntu>
                                     
                                     <https://help.ubuntu.com/community/Minicom>
  --------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------

<span id="O_515" class="anchor"><span id="_Toc456790862" class="anchor"></span></span>Terms and Abbreviations
-------------------------------------------------------------------------------------------------------------

<span id="_Toc456536729" class="anchor"></span>Table 2: Glossary

  Term                         Description
  ---------------------------- -------------------------------------------------------------
  Source/Trx                   Transmitter
  Sink/Rx/Downstream devices   Receiver
  TV                           Television
  DUT                          Device under test
  AVR                          AV Receiver
  TZ                           ARM Trust Zone
  HLOS                         High Level Operating System (e.g. Android or Windows Phone)

<span id="O_516" class="anchor"><span id="_Toc396212553" class="anchor"><span id="_Toc408227892" class="anchor"><span id="_Toc456790863" class="anchor"></span></span></span></span>Preliminary actions
-------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------

Before start running tests please do:

1.  Read the VDD for Demands, changes, bug fixes and comments.

2.  Make sure you have the correct device for tests.

3.  Verify Release package matches documents description. Relevant
    documents should be placed under:

    1.  HDCP/Documents

    2.  QA\_TST/Documents

    3.  If package does not have required documents, as a workaround it
        is possible to look for missing documents into [SW
        Documents](http://master/RnD/Products/Forms/AllItems.aspx?RootFolder=%2fRnD%2fProducts%2fCP%2fLink%20Protection%2fHDCP%2fSW%20Documents%2fDeliverables&FolderCTID=0x0120008C20BA6ADE051A459D53F6D037ED0A39&View=%7b52657E07-5F39-40CC-AC44-3C9578ACA27F%7d) 
        or [QA
        Documents](http://master/RnD/Products/Forms/AllItems.aspx?RootFolder=%2fRnD%2fProducts%2fCP%2fLink%20Protection%2fHDCP%2fQA%20Documents%2fDeliverables&FolderCTID=0x0120008C20BA6ADE051A459D53F6D037ED0A39&View=%7b52657E07-5F39-40CC-AC44-3C9578ACA27F%7d)

<span id="_Preparation_to_testing" class="anchor"><span id="_Toc456790864" class="anchor"></span></span>Preparation to testing
------------------------------------------------------------------------------------------------------------------------------

1.  Steps 2-6 are prerequisites for E2E tests. These steps are done as
    well as part of the QA Cycle.

2.  Install new supplied package according to [HDCP developer
    guide](http://master/RnD/Products/Forms/AllItems.aspx?RootFolder=%2fRnD%2fProducts%2fCP%2fLink%20Protection%2fHDCP%2fSW%20Documents%2fDeliverables&FolderCTID=0x0120008C20BA6ADE051A459D53F6D037ED0A39&View=%7b52657E07-5F39-40CC-AC44-3C9578ACA27F%7d)
    (is platform dependent document).

3.  Install QA Package according to [HDCP testing
    guide](http://master/RnD/Products/CP/Link%20Protection/HDCP/QA%20Documents/Internal/BUILDING%20HDCP%20QA%20PACKAGE.docx)

4.  Ensure that setup of HDCP configuration file is HDCP version
    2.2: DxHdcpVer=3.

5.  6.  7.  Provisioning of the device:

    1.  Both devices must use same key type (see next chapters). Refer
        to table 2.1 for the key type of every Sink side device in
        stock, and use the corresponding TZ App and HDCP on the
        source device.

    2.  The difference between test (facsimile) & production keys are:

        1.  Test keys are public and part of HDCP spec.

        2.  Production keys are secret and generated by DCP.

        3.  

    3.  Currently ARM Israel decided to use only facsimile (test) keys
        for HDCP testing.

    4.  In order to be able to test production TZ app of HDCP Source it
        is possible to use the following workaround:

        1.  On Source side:

            1.  Install HDCP HLOS and test TZ app

            2.  Do provisioning with facsimile (test) keys

            3.  Install HDCP production TZ app

        2.  Connect Source device against production 3rd party Sink
            device (the 3rd party Sink device is pre-provisioned using
            production keys)

        3.  Do relevant tests – see chapter ‎4 below. In this case, HDCP
            will pass authentication, but instead of screen mirroring
            picture, will appear a black screen on TV or monitor
            connected to the Sink device.

    5.  If Source device is provisioned with production keys & Sink
        device provisioned with test keys – the HDCP authentication
        expected to fail due to RSA signature verification failure.

    6.  3rd party production devices pre-provisioned using production
        keys on factory.

        3rd party development devices have possibility to switch between
        test and production keys, refer to table 2.1.

8.  Perform provisioning:

    1.  Perform provisioning on Android DUT (mostly by running External
        BB tests see in HDCP testing guide).

    2.  1.  For Transmitter side only, enough to run from test menu:

\[1\]–Provisioning

\[2\]-Provisioning with CEK with receiver certificate version 2.2.

1.  If need to test Sink side of DUT, must to run from test menu:

\[8\]-\[Settings\]

\[1\]-Set Sink Provisioning format 2.2

1.  2.  3.  On Qualcomm Windows Phone DUT provisioning may performed by
    [QCPhoneProvTool](http://172.16.7.200/CP/PRODUCTS/HA/KB/HDCP_WinTH_Guide?highlight=%28QCPhoneProvTool%29#Provisioning)
    (Qualcomm provisioning application)

or by ProvApp (ARM provisioning simulator application).

1.  HDCP devices can be Source and Qualcomm on latest versions of
    Android support Sink function too. As a Result, will perform tests
    for both sides: Trx & Rx.

2.  1.  2.  3.  

3.  <span id="_Toc456622878" class="anchor"><span id="_Toc456697746"
    class="anchor"><span id="_Toc456697787" class="anchor"><span
    id="_Toc456697828" class="anchor"><span id="_Toc456790869"
    class="anchor"></span></span></span></span></span>

4.  5.  6.  

<span id="_Sink_devices" class="anchor"><span id="_Toc456790873" class="anchor"></span></span>Sink side devices
===============================================================================================================

<span id="_Stock_of_Sink" class="anchor"><span id="_Toc456790874" class="anchor"></span></span>Stock of Sink devices
--------------------------------------------------------------------------------------------------------------------

<span id="_Toc456536730" class="anchor"></span>Table 3: 3^rd^ party
devices in stock

  **Device**                                                                                                                                       **Device Version**                                           **HDCP2 version**
  ------------------------------------------------------------------------------------------------------------------------------------------------ ------------------------------------------------------------ -------------------
  Cavium Dongle PureVu™ CNW6611L (Configurable: test or production keys) how to [check WIKI pages](http://172.16.7.200/CP/PRODUCTS/HDCP/DONGLES)   WD:44D2-6611LTMS128                                          2.1
  Samsung SmartTV UHN32F5500 (production keys)                                                                                                     11180                                                        2.1
  Samsung Allshare Cast Dongle (production keys)                                                                                                   EAD-T10 (EDEGSTD)                                            2.2
  Qualcomm MSM8996 device (test keys)                                                                                                              Qualcomm WFD client application configured as an HDCP Sink   2.2

<span id="_Toc408227895" class="anchor"><span id="_Toc456790875" class="anchor"></span></span>Setup of Sink devices
-------------------------------------------------------------------------------------------------------------------

1.  To activate Receiver devices (for e.g. dongles) must to connect by
    HDMI cable to TV (except QC device) and connect to power with
    USB cable. Cavium dongle can be connected to PC by
    [Minicom](#O_514).

In this picture shown connected Cavium Dongle.

![](media/image3.jpeg){width="5.048611111111111in"
height="2.5388888888888888in"}

In next picture shown connected Dongle Samsung.

![](media/image4.jpeg){width="4.2558902012248465in"
height="2.967361111111111in"}

1.  Connect dongle to power by USB cable.

2.  Connect dongle to TV by HDMI cable

3.  On TV choose needed source (for e.g. HDMI 1 or HDMI 2)

4.  After appear on TV screen notification from dongle, ready to
    connect, follow to next [part](#_Source_Side)

5.  Before using Samsung TV in Sink side on DUT in Source side in
    DXHDCP.cfg change AvoidTimeouts=True

6.  If using QC DUT ensure that /system/etc/wfdconfigsink.xml
    configured:

&lt;!-- enable HDCP by default --&gt;

&lt;ContentProtection&gt;

&lt;Valid&gt;1&lt;/Valid&gt;

&lt;!--

Valid values WFD\_HDCP\_2\_0,

WFD\_HDCP\_2\_1 and WFD\_HDCP\_2\_2

> read more: [HDCP Enabled](http://172.16.7.200/CP/PRODUCTS/HDCP)

1.  Than lunch “WFD client” application.

![](media/image5.png){width="3.935416666666667in"
height="2.656241251093613in"}

1.  Choose Sink.

![](media/image6.png){width="3.0570931758530184in"
height="1.3946248906386702in"}

![](media/image7.png){width="4.634027777777778in"
height="3.470138888888889in"}

1.  Tap “search”, then application finished:

![](media/image8.png){width="4.675324803149606in"
height="1.3763888888888889in"}

1.  Choose desired device from list of founded devices tap “connect” and
    “start session”

<span id="_Source_Side" class="anchor"><span id="_Source_Side_devices" class="anchor"><span id="_Toc456790876" class="anchor"></span></span></span>Source Side devices
======================================================================================================================================================================

MediaTek
--------

1.  Model: k55v1\_64\_tee / Android version: 6.0 (may change)

2.  Tap on icon “Settings”:

> ![](media/image9.png){width="3.727777777777778in"
> height="3.0416666666666665in"}

1.  Tap on “Display”:

> ![](media/image10.png){width="3.6805555555555554in"
> height="2.1847222222222222in"}

1.  Choose “Cast”:

> ![](media/image11.png){width="4.28991469816273in"
> height="3.753731408573928in"}

1.  Enable wireless display:

> ![](media/image12.png){width="3.936489501312336in"
> height="2.5671642607174103in"}

1.  Choose from appeared devices list, needed Sink & tap connect.

Qualcomm
--------

1.  All family of QC devices can be used for E2E tests source side.

2.  QC device have two ways to establish connection:

    1.  Similar to MTK via settings and Cast Display.

    2.  By application “WFD client”.

3.  **NOTE:** Before beginning E2E tests check:

    1.  libwfdhdcpcp.so located: /system/vendor/lib64/ &
        /system/vendor/lib/ compiled with HDCP support enabled, for
        details see [HDCP Enabled](http://172.16.7.200/CP/PRODUCTS/HDCP)

    2.  wfdconfig.xml located in /system/etc, configured:

&lt;!-- enable HDCP by default --&gt;

&lt;ContentProtection&gt;

&lt;Valid&gt;1&lt;/Valid&gt;

&lt;!--

Valid values WFD\_HDCP\_2\_0,

WFD\_HDCP\_2\_1 and WFD\_HDCP\_2\_2

1.  Connecting via “WFD client”:

    1.  Tap on WFD client icon:

> ![](media/image5.png){width="3.935416666666667in"
> height="2.656241251093613in"}

1.  Choose Source:

> ![](media/image6.png){width="3.9359284776902888in"
> height="1.798507217847769in"}
>
> ![](media/image13.png){width="4.880379483814523in"
> height="2.8644542869641296in"}

1.  Chose by tap from devices list needed Sink device:

> ![](media/image14.png){width="4.857638888888889in"
> height="2.9328357392825897in"}

1.  Tap on “Connect” & “Start session”

> ![](media/image15.png){width="4.895522747156606in"
> height="2.2756944444444445in"}
>
> ![](media/image16.png){width="4.678472222222222in"
> height="2.985074365704287in"}

1.  After “start session” tapped, connection will be established.

Windows devices
---------------

1.  Before begin a preparation of DUT check [readme
    file](https://github.com/ARMmbed/ta-TZInfra/blob/master/docs/windows-threshold/README.md)
    and wiki page.

2.  Copy the HDCP dll file to the device
    under C:\\Windows\\system32\\DxHdcp\_WoS\_WP.dll and rename to
    OemHdcp.dll

3.  DLL must be PE signed in Microsoft, in order to be able to run as
    part of the protected process.

4.  For more knowledge about HDCP logging on Windows devices read here.

5.  Connecting:

    1.  Select the "Settings" menu on the Windows DUT:
        ![](media/image17.jpeg){width="3.9316786964129484in"
        height="3.5069444444444446in"}

    2.  Select the "Connect" menu:
        ![](media/image18.jpeg){width="4.149254155730533in"
        height="3.276388888888889in"}
        ![](media/image19.jpeg){width="4.0368055555555555in"
        height="1.8805971128608925in"}

    3.  Select the device you wish to run the test against him:
        ![](media/image20.jpeg){width="3.589583333333333in"
        height="3.022222222222222in"}

    4.  Ensure that the DUT is connected to the selected remote device:
        ![](media/image21.jpeg){width="3.5743055555555556in"
        height="3.2090277777777776in"}

<span id="_Test_cases_Source" class="anchor"><span id="_Ref456777333" class="anchor"><span id="_Toc456790880" class="anchor"></span></span></span>Test cases - Source side
==========================================================================================================================================================================

**Note:** Most of tests will performed, when will have installed on DUT:
HDCP HLOS & Trust Zone (TZ app) with test keys.

If in some test cases, will required DUT with installed HDCP HLOS &
Trust Zone (TZ app) with production keys, read chapter 1.5.

<span id="_Toc408227904" class="anchor"><span id="_Toc456790881" class="anchor"></span></span>**Connection between Dongle & DUT (test keys)**
---------------------------------------------------------------------------------------------------------------------------------------------

+--------------------------------------+--------------------------------------+
| **\                                  | **Connection between Dongle and DUT  |
| Test ID:**                           | (test keys) **                       |
+======================================+======================================+
| **Priority:**                        | **High Priority**                    |
+--------------------------------------+--------------------------------------+
| **Purpose:**                         | **To test: success of HDCP           |
|                                      | connection with test keys. **        |
+--------------------------------------+--------------------------------------+
| **Relevant OS: **                    | **Android, Windows 8.1 & up**        |
+--------------------------------------+--------------------------------------+
| **DUT Transmitter/Sink: **           | **Source side**                      |
+--------------------------------------+--------------------------------------+
| **Preconditions:**                   | -   **HDCP Source is installed,      |
|                                      |     provisioned and configured as    |
|                                      |     HDCP 2.2 Dongle connected        |
|                                      |     to TV.**                         |
|                                      |                                      |
|                                      | -   **Sink device connected to TV or |
|                                      |     monitor using HDMI cable.**      |
|                                      |                                      |
|                                      | -   **DUT & Dongle in same WI-FI     |
|                                      |     network**                        |
|                                      |                                      |
|                                      | -   -   -                            |
+--------------------------------------+--------------------------------------+
| **Relevant dongles:**                | **Cavium (configured to use test     |
|                                      | keys); Qualcomm MSM8996 configured   |
|                                      | as Sink** **to use test keys**       |
+--------------------------------------+--------------------------------------+

  ---------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------
  **1.**   ***Connect devices via WFD/Projects***                                 ***Connection established: Have mirroring between Trx & TV ***
  -------- ---------------------------------------------------------------------- -------------------------------------------------------------------------------------------------------------------------
  **2.**   ***Twist the device***                                                 ***Devices stay connected: Have mirroring between Trx & TV***

  **3.**   ***Attempt to play any content (for e.g. from YouTube) ***             ***Smoothly playback: Have mirroring between Trx & TV***

  **4.**   ***Disconnect*** ***the Devices (by type end of connection)***         ***Devices disconnected: Mirroring between Trx & TV stopped ***

  **5.**   ***Check in logcat (for android device)***:                            ***This logs*** ***do include messages: DX\_HDCP\_CONNECTION\_STATE\_AUTHENTICATED; DX\_HDCP\_CIPHER\_DATA succeeded***
                                                                                  
           ***On Windows DUT check in files: c:\\data\\test\\bin\\HDCP\_TSMT***   
  ---------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------

<span id="_Toc408227905" class="anchor"><span id="_Toc456790882" class="anchor"></span></span>**Connection between Dongle & DUT (production keys)**
---------------------------------------------------------------------------------------------------------------------------------------------------

+--------------------------------------+--------------------------------------+
| **\                                  | **Connection between Dongle and DUT  |
| Test ID:**                           | (production keys)**                  |
+======================================+======================================+
| **Priority:**                        | **High Priority**                    |
+--------------------------------------+--------------------------------------+
| **Purpose:**                         | **to test: success of HDCP           |
|                                      | connection with production keys. **  |
+--------------------------------------+--------------------------------------+
| **Relevant OS:**                     | **Android, Windows 8.1 & up**        |
+--------------------------------------+--------------------------------------+
| **DUT Transmitter/Sink: **           | **Source side**                      |
+--------------------------------------+--------------------------------------+
| **Preconditions:**                   | -   **HDCP Source is installed,      |
|                                      |     provisioned and configured as    |
|                                      |     HDCP 2.2**                       |
|                                      |     **(production release)**         |
|                                      |     **Dongle connected to TV.**      |
|                                      |                                      |
|                                      | -   **Sink device connected to TV or |
|                                      |     monitor using HDMI cable.**      |
|                                      |                                      |
|                                      | -   **DUT & Dongle in same WI-FI     |
|                                      |     network**                        |
|                                      |                                      |
|                                      | -   -   -                            |
+--------------------------------------+--------------------------------------+
| **Relevant dongles:**                | **Samsung SmartTV; Samsung Allshare  |
|                                      | Cast Dongle; Cavium Dongle           |
|                                      | (configured with production keys)**  |
+--------------------------------------+--------------------------------------+

  ---------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------
  **1.**   ***Connect devices via WFD/Projects***                                       ***Connection established: Have no mirroring between TV & Rx (black screen)***
  -------- ---------------------------------------------------------------------------- -------------------------------------------------------------------------------------------------------------------
  **2.**   ***Twist the device***                                                       ***Devices stay connected: Have no mirroring between TV & Rx (black screen)***

  **3.**   ***Disconnect the Devices (by type end of connection)***                     ***Devices disconnected: TV backed to self-screen from black screen***

  **4.**   ***Check in logcat (for android device)***:                                  ***This logs do include messages: DX\_HDCP\_CONNECTION\_STATE\_AUTHENTICATED; DX\_HDCP\_CIPHER\_DATA succeeded***
                                                                                        
           ***On Windows DUT*** ***check in files: c:\\data\\test\\bin\\HDCP\_TSMT***   
  ---------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------

<span id="_Toc408227906" class="anchor"><span id="_Toc456790883" class="anchor"></span></span>**Reconnection between dongle & DUT (1)**
---------------------------------------------------------------------------------------------------------------------------------------

+--------------------------------------+--------------------------------------+
| **\                                  | **Reconnection between Dongle and    |
| Test ID:**                           | DUT after valid disconnection **     |
+======================================+======================================+
| **Priority:**                        | **High Priority**                    |
+--------------------------------------+--------------------------------------+
| **Purpose:**                         | **To test: Ability of DUT reconnect  |
|                                      | after valid disconnection.**         |
+--------------------------------------+--------------------------------------+
| **Relevant OS:**                     | **Android, Windows 8.1 & up**        |
+--------------------------------------+--------------------------------------+
| **DUT Transmitter/Sink: **           | **Source side**                      |
+--------------------------------------+--------------------------------------+
| **Preconditions:**                   | -   **HDCP Source is installed,      |
|                                      |     provisioned and configured as    |
|                                      |     HDCP 2.2 Dongle connected        |
|                                      |     to TV.**                         |
|                                      |                                      |
|                                      | -   **Sink device connected to TV or |
|                                      |     monitor using HDMI cable.**      |
|                                      |                                      |
|                                      | -   **DUT & Dongle in same WI-FI     |
|                                      |     network**                        |
|                                      |                                      |
|                                      | -   -   -                            |
+--------------------------------------+--------------------------------------+
| **Relevant dongles:**                | **Cavium (configured with test       |
|                                      | keys); Qualcomm MSM8996 configured   |
|                                      | as Sink** to use test keys           |
+--------------------------------------+--------------------------------------+

  -----------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------
  **1.**   ***Connect devices via WFD/Projects***                                   ***Connection established: Have mirroring between Trx & TV ***
  -------- ------------------------------------------------------------------------ -------------------------------------------------------------------------------------------------------------------------
  **2.**   ***Twist the device***                                                   ***Devices stay connected: Have mirroring between Trx & TV***

  **3.**   ***Attempt to play any content (for e.g. from YouTube) ***               ***Smoothly playback: Have mirroring between Trx & TV***

  **4.**   ***Disconnect the Devices (by*** ***tap “end of connection” button)***   ***Devices disconnected: Mirroring between Trx & TV stopped***

  **5.**   ***Connect devices via WFD/Projects***                                   ***Connection established: Have mirroring between Trx & TV ***

  **6.**   ***Twist the device***                                                   ***Devices stay connected: Have mirroring between Trx & TV***

  **7.**   ***Disconnect*** ***the Devices (by type end of connection)***           ***Devices disconnected: Mirroring between Trx & TV stopped***

  **8.**   ***Repeat steps*** ***1-7*** ***on several occasions***                  ***Everything is performed with no issues***

  **9.**   ***Check in logcat (for android device)***:                              ***This logs*** ***do include messages: DX\_HDCP\_CONNECTION\_STATE\_AUTHENTICATED; DX\_HDCP\_CIPHER\_DATA succeeded***
                                                                                    
           ***On Windows DUT check in files: c:\\data\\test\\bin\\HDCP\_TSMT***     
  -----------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------

<span id="_Toc408227907" class="anchor"><span id="_Toc456790884" class="anchor"></span></span>**Reconnection between dongle & DUT(2)**
--------------------------------------------------------------------------------------------------------------------------------------

+--------------------------------------+--------------------------------------+
| **\                                  | **Reconnection between Dongle and    |
| Test ID:**                           | DUT after non-valid disconnection ** |
+======================================+======================================+
| **Priority:**                        | **High Priority**                    |
+--------------------------------------+--------------------------------------+
| **Purpose:**                         | **to test: Ability of DUT reconnect  |
|                                      | after non-valid disconnection.**     |
+--------------------------------------+--------------------------------------+
| **Relevant OS: **                    | **Android, Windows 8.1 & up**        |
+--------------------------------------+--------------------------------------+
| **DUT Transmitter/Sink: **           | **Source side**                      |
+--------------------------------------+--------------------------------------+
| **Preconditions:**                   | -   **HDCP Source is installed,      |
|                                      |     provisioned and configured as    |
|                                      |     HDCP 2.2 Dongle connected        |
|                                      |     to TV.**                         |
|                                      |                                      |
|                                      | -   **Sink device connected to TV or |
|                                      |     monitor using HDMI cable.**      |
|                                      |                                      |
|                                      | -   **DUT & Dongle in same WI-FI     |
|                                      |     network**                        |
|                                      |                                      |
|                                      | -   -   -                            |
+--------------------------------------+--------------------------------------+
| **Relevant dongles:**                | **Cavium (configured test keys)**;   |
|                                      | **Qualcomm MSM8996 configured as     |
|                                      | Sink** **to use test keys**          |
+--------------------------------------+--------------------------------------+

  ---------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------
  **1.**   ***Connect devices via WFD/Projects***                                                                     ***Connection established: Have mirroring between Trx & TV ***
  -------- ---------------------------------------------------------------------------------------------------------- -------------------------------------------------------------------------------------------------------------------
  **2.**   ***Twist the device***                                                                                     ***Devices stay connected: Have mirroring between Trx & TV***

  **3.**   ***Attempt to play any content (for e.g. from YouTube) ***                                                 ***Smoothly playback: Have mirroring between Trx & TV***

  **4.**   ***Disconnect*** ***the*** ***Trx and Sink*** ***(by pooling out cable or dongle from HDMI connector)***   ***Devices disconnected: Mirroring between Trx &* *TV stopped***
                                                                                                                      
                                                                                                                      ***On DUT: error message ***

  **5.**   ***Connect devices via WFD/Projects***                                                                     ***Connection established: Have mirroring between Trx & TV ***

  **6.**   ***Twist the device***                                                                                     ***Devices stay connected: Have mirroring between Trx & TV***

  **7.**   ***Disconnect*** ***the Devices (by stopping application)***                                               ***Devices disconnected: Mirroring between Trx & TV*** ***stopped***

  **8.**   ***Repeat steps 1-7 on several occasions***                                                                ***Everything is performed with no issues***

  **9.**   ***Check in logcat (for android device)***:                                                                ***This logs do include messages: DX\_HDCP\_CONNECTION\_STATE\_AUTHENTICATED; DX\_HDCP\_CIPHER\_DATA succeeded***
                                                                                                                      
           ***On Windows DUT check in files: c:\\data\\test\\bin\\HDCP\_TSMT***                                       
  ---------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------

<span id="_Toc408227908" class="anchor"><span id="_Toc456790885" class="anchor"></span></span>**Behavior of HDCP connection after update version (with no stored km)**
----------------------------------------------------------------------------------------------------------------------------------------------------------------------

+--------------------------------------+--------------------------------------+
| **\                                  | **Connection between Dongle and DUT  |
| Test ID:**                           | after update to new version (no      |
|                                      | stored km)**                         |
+======================================+======================================+
| **Priority:**                        | **High Priority**                    |
+--------------------------------------+--------------------------------------+
| **Purpose:**                         | **to test: Success of HDCP           |
|                                      | connection after update to new HDCP  |
|                                      | version (no used before) **          |
+--------------------------------------+--------------------------------------+
| **Relevant OS: **                    | **Android, Windows 8.1 & up**        |
+--------------------------------------+--------------------------------------+
| **DUT Transmitter/Sink: **           | **Source side**                      |
+--------------------------------------+--------------------------------------+
| **Preconditions:**                   | -   **HDCP Source is installed,      |
|                                      |     provisioned and configured as    |
|                                      |     HDCP 2.2 Dongle connected        |
|                                      |     to TV.**                         |
|                                      |                                      |
|                                      | -   **Sink device connected to TV or |
|                                      |     monitor using HDMI cable.**      |
|                                      |                                      |
|                                      | -   **DUT & Dongle in same WI-FI     |
|                                      |     network**                        |
|                                      |                                      |
|                                      | -   -   -                            |
+--------------------------------------+--------------------------------------+
| **Relevant dongles:**                | **Cavium (configured test keys)**;   |
|                                      | **Qualcomm MSM8996 configured as     |
|                                      | Sink** **to use test keys**          |
+--------------------------------------+--------------------------------------+

  ------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------
  **1.**   ***Execute provisioning on DUT ***                                                                           ***DUT is provisioned***
  -------- ------------------------------------------------------------------------------------------------------------ --------------------------------------------------------------------------------------------------------------------------
  **2.**   ***Install on DUT the current version:*** ***Trust Zone*** ***(test release); hlos*** ***(test release)***   ***DUT ready for E2E ***

  **3.**   ***Connect devices via WFD/Projects***                                                                       ***Connection established with no errors, have mirroring between Trx & TV***

  **4.**   ***Disconnect*** ***the Devices (by type end of connection)***                                               ***Devices disconnected***

  **5.**   ***Check in logcat (for android device)***:                                                                  ***This logs*** ***do include messages: DX\_HDCP\_CONNECTION\_STATE\_AUTHENTICATED; DX\_HDCP\_CIPHER\_DATA succeeded ***
                                                                                                                        
           ***On Windows DUT check in files: c:\\data\\test\\bin\\HDCP\_TSMT***                                         
  ------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------

<span id="_Toc408227910" class="anchor"></span>

**Behavior of HDCP connection after update version (with stored km)**
---------------------------------------------------------------------

+--------------------------------------+--------------------------------------+
| **\                                  | **Connection between Dongle and DUT  |
| Test ID:**                           | after update (with stored km) **     |
+======================================+======================================+
| **Priority:**                        | **High Priority**                    |
+--------------------------------------+--------------------------------------+
| **Purpose:**                         | **to test: Success of HDCP           |
|                                      | connection after update to HDCP new  |
|                                      | version (used before) **             |
+--------------------------------------+--------------------------------------+
| **Relevant OS: **                    | **Android, Windows 8.1 & up**        |
+--------------------------------------+--------------------------------------+
| **DUT Transmitter/Sink: **           | **Source side**                      |
+--------------------------------------+--------------------------------------+
| **Preconditions:**                   | -   **HDCP Source is installed,      |
|                                      |     provisioned and configured as    |
|                                      |     HDCP 2.2 Dongle connected        |
|                                      |     to TV.**                         |
|                                      |                                      |
|                                      | -   **Sink device connected to TV or |
|                                      |     monitor using HDMI cable.**      |
|                                      |                                      |
|                                      | -   **DUT & Dongle in same WI-FI     |
|                                      |     network**                        |
|                                      |                                      |
|                                      | -   -   -                            |
+--------------------------------------+--------------------------------------+
| **Relevant dongles:**                | **Cavium (configured test keys)**;   |
|                                      | **Qualcomm MSM8996 configured as     |
|                                      | Sink**                               |
+--------------------------------------+--------------------------------------+

  ------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------
  **1.**   ***Execute provisioning on DUT with previous version of HDCP***                                        ***DUT is provisioned ***
  -------- ------------------------------------------------------------------------------------------------------ --------------------------------------------------------------------------------------------------------------------
  **2.**   ***Connect devices via WFD/Projects***                                                                 ***Connection established with no errors, have mirroring between Trx & TV***

  **3.**   ***Disconnect*** ***the Devices (by*** ***tap “end of connection” button)***                           ***Devices disconnected***

  **4.**   ***Install on DUT the current version: Trust Zone*** ***(test release); hlos*** ***(test release)***   ***DUT ready for E2E ***

  **5.**   ***Connect devices via WFD/Projects***                                                                 ***Connection established with no errors, have mirroring between Trx & TV***

  **6.**   ***Disconnect*** ***the Devices (by*** ***tap “end of connection” button)***                           ***Devices disconnected***

  **7.**   ***Check in logcat (for android device)***:                                                            ***This logs do include messages: DX\_HDCP\_CONNECTION\_STATE\_AUTHENTICATED; DX\_HDCP\_CIPHER\_DATA succeeded ***
                                                                                                                  
           ***On Windows DUT check in files: c:\\data\\test\\bin\\HDCP\_TSMT***                                   
  ------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------

**Behavior of HDCP during connection/disconnection**
----------------------------------------------------

+--------------------------------------+--------------------------------------+
| **\                                  | **Behavior of HDCP** **connection    |
| Test ID:**                           | between TV and DUT** **while plural  |
|                                      | disconnections **                    |
+======================================+======================================+
| **Priority:**                        | **High Priority**                    |
+--------------------------------------+--------------------------------------+
| **Purpose:**                         | **To test an ability of Trx to**     |
|                                      | **plural** **switching of** **TV     |
|                                      | channels when working** **against    |
|                                      | Sink device.**                       |
+--------------------------------------+--------------------------------------+
| **Relevant OS: **                    | **Android, Windows 8.1 & up**        |
+--------------------------------------+--------------------------------------+
| **DUT Transmitter/Sink: **           | **Source side**                      |
+--------------------------------------+--------------------------------------+
| **Preconditions:**                   | -   **HDCP Source is installed,      |
|                                      |     provisioned and configured as    |
|                                      |     HDCP 2.2**                       |
|                                      |                                      |
|                                      | -   -   **Dongle connected to**      |
|                                      |     **TV.**                          |
|                                      |                                      |
|                                      | -   **Sink device connected to TV or |
|                                      |     monitor using HDMI cable.**      |
|                                      |                                      |
|                                      | -   **DUT & Dongle in same WI-FI     |
|                                      |     network**                        |
+--------------------------------------+--------------------------------------+
| **Relevant dongles:**                | **Cavium (configured test keys)**;   |
|                                      | **Qualcomm MSM8996 configured as     |
|                                      | Sink**                               |
+--------------------------------------+--------------------------------------+

  -----------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------
  ***1.***   ***Connect DUT via WFD/Projects to dongle***                           ***Connection established: Have mirroring between Trx & TV ***
  ---------- ---------------------------------------------------------------------- -------------------------------------------------------------------------------------------------------------------------------------------------------
  ***2.***   ***Twist the device***                                                 ***Devices stay connected: Have mirroring between Trx & TV***

  ***3.***   ***Attempt to play any content*** ***(for e.g. from YouTube) ***       ***Smoothly playback: Have mirroring between Trx & TV***

  ***4.***   ***On*** ***TV change the source*** ***or*** ***channel***             ***Devices disconnected: Mirroring between Trx & TV stopped ***

  ***5.***   ***Change the source (channel) back***                                 ***NO mirroring between Trx & TV***

  ***6.***   ***Connect DUT via WFD/Projects to dongle***                           ***Connection established: Have mirroring between Trx & TV ***

  ***7.***   ***Disconnect*** ***the Devices (by type end of connection)***         ***Devices disconnected: Mirroring between Trx & TV stopped ***

  ***8.***   ***Repeat steps 1-7 on several occasions***                            ***Everything is performed with no issues***

  ***9.***   ***Check in logcat (for android device):***                            ***This logs*** ***do include messages: DX\_HDCP\_CONNECTION\_STATE\_AUTHENTICATED; DX\_HDCP\_CIPHER\_DATA succeeded; and between errors messages ***
                                                                                    
             ***On Windows DUT check in files: c:\\data\\test\\bin\\HDCP\_TSMT***   
  -----------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------

**Behavior of HDCP connection with TZ app test keys via HDMI AVR receiver**
---------------------------------------------------------------------------

+--------------------------------------+--------------------------------------+
| **\                                  | **Connection between TV and DUT via  |
| Test ID:**                           | AVR receiver** ( Trx test keys)      |
+======================================+======================================+
| **Priority:**                        | **High Priority**                    |
+--------------------------------------+--------------------------------------+
| **Purpose:**                         | **To test an ability of Trx to work  |
|                                      | against Sink device (test keys) with |
|                                      | more than one downstream devices.**  |
+--------------------------------------+--------------------------------------+
| **Relevant OS: **                    | **Android, Windows 8.1 & up**        |
+--------------------------------------+--------------------------------------+
| **DUT Transmitter/Sink: **           | **Source side**                      |
+--------------------------------------+--------------------------------------+
| **Preconditions:**                   | -   **HDCP Source is installed,      |
|                                      |     provisioned and configured as    |
|                                      |     HDCP 2.2 Dongle connected        |
|                                      |     to TV.**                         |
|                                      |                                      |
|                                      | -   **Sink device connected to AVR   |
|                                      |     **                               |
|                                      |                                      |
|                                      | -   **AVR connected to TV or monitor |
|                                      |     using HDMI cable.**              |
|                                      |                                      |
|                                      | -   **DUT & Dongle in same WI-FI     |
|                                      |     network**                        |
|                                      |                                      |
|                                      | -   -   -   -                        |
+--------------------------------------+--------------------------------------+
| **Relevant dongles:**                | **Cavium (configured test keys)**;   |
|                                      | **Qualcomm MSM8996 configured as     |
|                                      | Sink**                               |
+--------------------------------------+--------------------------------------+

  --------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------
  **1.**   ***Connect devices via WFD/Projects***                                 ***Connection established: Have mirroring between Trx & TV ***
  -------- ---------------------------------------------------------------------- ------------------------------------------------------------------------------------------------------------------
  **2.**   ***Twist the device***                                                 ***Devices stay connected: Have mirroring between Trx & TV***

  **3.**   ***Attempt to play any content*** ***(for e.g. from YouTube) ***       ***Smoothly playback: Have mirroring between Trx & TV***

  **4.**   ***Disconnect*** ***the Devices (by type end of connection)***         ***Devices disconnected: Mirroring between Trx & TV stopped***

  **5.**   ***Repeat steps 1-4 on several occasions***                            ***Everything is performed with no issues***

  **6.**   ***Check in logcat (for android device)***:                            ***The logs messages have lines: DX\_HDCP\_CONNECTION\_STATE\_AUTHENTICATED; DX\_HDCP\_CIPHER\_DATA succeeded***
                                                                                  
           ***On Windows DUT check in files: c:\\data\\test\\bin\\HDCP\_TSMT***   
  --------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------

<span id="_Toc408227911" class="anchor"><span id="_Toc456790889" class="anchor"></span></span>**Behavior of multiple HDCP connection with TZ app production keys via AVR receiver**
-----------------------------------------------------------------------------------------------------------------------------------------------------------------------------------

+--------------------------------------+--------------------------------------+
| **\                                  | **Connection between TV and DUT via  |
| Test ID:**                           | AV receiver** (Trx production keys)  |
+======================================+======================================+
| **Priority:**                        | **High Priority**                    |
+--------------------------------------+--------------------------------------+
| **Purpose:**                         | **To test an ability of Trx to work  |
|                                      | against Sink device (production      |
|                                      | keys) with more than one downstream  |
|                                      | devices.**                           |
+--------------------------------------+--------------------------------------+
| **Relevant OS: **                    | **Android, Windows 8.1 & up**        |
+--------------------------------------+--------------------------------------+
| **DUT Transmitter/Sink: **           | **Source side**                      |
+--------------------------------------+--------------------------------------+
| **Preconditions:**                   | -   **HDCP Source is installed,      |
|                                      |     provisioned and configured as    |
|                                      |     HDCP 2.2 (production release)**  |
|                                      |     **Dongle connected to TV.**      |
|                                      |                                      |
|                                      | -   **Sink device connected to AVR   |
|                                      |     **                               |
|                                      |                                      |
|                                      | -   **AVR connected to TV or monitor |
|                                      |     using HDMI cable.**              |
|                                      |                                      |
|                                      | -   **DUT & Dongle in same WI-FI     |
|                                      |     network**                        |
|                                      |                                      |
|                                      | -   -   -                            |
+--------------------------------------+--------------------------------------+
| **Relevant dongles:**                | > **Samsung SmartTV; Samsung         |
|                                      | > Allshare Cast Dongle; Cavium       |
|                                      | > (configured production keys)**     |
+--------------------------------------+--------------------------------------+

  ---------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------
  **1.**   ***Connect devices via WFD/Projects***                                 ***Connection established: Have no mirroring between Trx & TV (black screen)***
  -------- ---------------------------------------------------------------------- -------------------------------------------------------------------------------------------------------------------
  **2.**   ***Twist the device***                                                 ***Devices stay connected: Have no mirroring between Trx & TV (black screen)***

  **3.**   ***Disconnect the Devices (by type end of connection)***               ***Devices disconnected: TV backed to self-screen from black screen.***

  **4.**   ***Check in logcat (for android device)***:                            ***This logs do include messages: DX\_HDCP\_CONNECTION\_STATE\_AUTHENTICATED; DX\_HDCP\_CIPHER\_DATA succeeded***
                                                                                  
           ***On Windows DUT check in files: c:\\data\\test\\bin\\HDCP\_TSMT***   

  **5.**   ***Repeat steps 1-4 on several occasions***                            ***Everything is performed with no issues***

  **6.**   ***Check in logcat (for android device)***:                            ***The logs messages have lines: DX\_HDCP\_CONNECTION\_STATE\_AUTHENTICATED; DX\_HDCP\_CIPHER\_DATA succeeded***
                                                                                  
           ***On Windows DUT check in files: c:\\data\\test\\bin\\HDCP\_TSMT***   
  ---------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------

**Behavior of HDCP during plural of connection/disconnection** 
---------------------------------------------------------------

+--------------------------------------+--------------------------------------+
| **\                                  | **Behavior of HDCP connection        |
| Test ID:**                           | between TV and DUT while plural      |
|                                      | disconnections **                    |
+======================================+======================================+
| **Priority:**                        | **High Priority**                    |
+--------------------------------------+--------------------------------------+
| **Purpose:**                         | **To test an ability of Trx to       |
|                                      | switch TV channels when working      |
|                                      | against Sink device with more than   |
|                                      | one downstream devices.**            |
+--------------------------------------+--------------------------------------+
| **Relevant OS: **                    | **Android, Windows 8.1 & up**        |
+--------------------------------------+--------------------------------------+
| **DUT Transmitter/Sink: **           | **Source side**                      |
+--------------------------------------+--------------------------------------+
| **Preconditions:**                   | -   **HDCP Source is installed,      |
|                                      |     provisioned and configured as    |
|                                      |     HDCP 2.2 Dongle connected        |
|                                      |     to TV.**                         |
|                                      |                                      |
|                                      | -   **Sink device connected to AVR   |
|                                      |     **                               |
|                                      |                                      |
|                                      | -   **AVR connected to TV or monitor |
|                                      |     using HDMI cable.**              |
|                                      |                                      |
|                                      | -   **DUT & Dongle in same WI-FI     |
|                                      |     network**                        |
+--------------------------------------+--------------------------------------+
| **Relevant dongles:**                | **Cavium (configured test keys)**;   |
|                                      | **Qualcomm MSM8996 configured as     |
|                                      | Sink**                               |
+--------------------------------------+--------------------------------------+

  -----------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------
  ***1.***   ***Connect DUT via WFD/Projects to dongle***                           ***Connection established: Have mirroring between Trx & TV ***
  ---------- ---------------------------------------------------------------------- -------------------------------------------------------------------------------------------------------------------------------------------------
  ***2.***   ***Twist the device***                                                 ***Devices stay connected: Have mirroring between Trx & TV***

  ***3.***   ***Attempt to play any content (for e.g. from YouTube) ***             ***Smoothly playback: Have mirroring between Trx & TV***

  ***4.***   ***On TV change the source or channel***                               ***Devices disconnected: Mirroring between Trx & TV stopped ***

  ***5.***   ***Change the source (channel) back***                                 ***NO mirroring between Trx & TV***

  ***6.***   ***Connect DUT via WFD/Projects to dongle***                           ***Connection established: Have mirroring between Trx & TV ***

  ***7.***   ***Disconnect the Devices (by type end of connection)***               ***Devices disconnected: Mirroring between Trx & TV stopped ***

  ***8.***   ***Repeat steps 1-7 on several occasions***                            ***Everything is performed with no issues***

  ***9.***   ***Check in logcat (for android device):***                            ***This logs do include messages: DX\_HDCP\_CONNECTION\_STATE\_AUTHENTICATED; DX\_HDCP\_CIPHER\_DATA succeeded; and between errors messages ***
                                                                                    
             ***On Windows DUT check in files: c:\\data\\test\\bin\\HDCP\_TSMT***   
  -----------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------

<span id="_Test_cases_Sink" class="anchor"><span id="_Toc456790891" class="anchor"></span></span>Test cases - Sink side
=======================================================================================================================

**Connection between Source device** **& DUT **
-----------------------------------------------

+--------------------------------------+--------------------------------------+
| **\                                  | **Connection between Source device** |
| Test ID:**                           | **and DUT **                         |
+======================================+======================================+
| **Priority:**                        | **High Priority**                    |
+--------------------------------------+--------------------------------------+
| **Purpose:**                         | **To test: success of HDCP           |
|                                      | connection with test keys. **        |
+--------------------------------------+--------------------------------------+
| **Relevant OS: **                    | **Android**                          |
+--------------------------------------+--------------------------------------+
| **DUT Transmitter/Sink: **           | **Sink** **side**                    |
+--------------------------------------+--------------------------------------+
| **Preconditions:**                   | -   **HDCP Source** **& Sink** **is  |
|                                      |     installed, provisioned and       |
|                                      |     configured as HDCP 2.2 Dongle    |
|                                      |     connected to TV.**               |
|                                      |                                      |
|                                      | -   **Sink device connected to TV or |
|                                      |     monitor using HDMI cable.**      |
|                                      |                                      |
|                                      | -   **DUT & Source device in same    |
|                                      |     WI-FI network**                  |
+--------------------------------------+--------------------------------------+
| **Relevant source side devices:**    | **MediaTek k55v1\_64\_tee; Qualcomm  |
|                                      | MSM8996 (HLOS android); Qualcomm     |
|                                      | MSM8996 (HLOS windows)**             |
+--------------------------------------+--------------------------------------+

  **1.**   ***Connect devices via WFD/Projects***                                ***Connection established: Have mirroring between Trx & TV ***
  -------- --------------------------------------------------------------------- -------------------------------------------------------------------------------------------------------------------
  **2.**   ***Twist the device***                                                ***Devices stay connected: Have mirroring between Trx & TV***
  **3.**   ***Attempt to play any content (for e.g. from YouTube) ***            ***Smoothly playback: Have mirroring between Trx & TV***
  **4.**   ***Disconnect the Devices (by*** ***tap*** ***end of connection)***   ***Devices disconnected: Mirroring between Trx & TV stopped ***
  **5.**   ***Check in logcat (for android device)***:                           ***This logs do include messages: DX\_HDCP\_CONNECTION\_STATE\_AUTHENTICATED; DX\_HDCP\_CIPHER\_DATA succeeded***

<span id="_Toc456790893" class="anchor"></span>

<span id="_Toc456790894" class="anchor"></span>

<span id="_Toc456790895" class="anchor"></span>

<span id="_Toc456790896" class="anchor"></span>

<span id="_Toc456790897" class="anchor"></span>

<span id="_Toc456790898" class="anchor"></span>

<span id="_Toc456790899" class="anchor"></span>

<span id="_Toc456790900" class="anchor"></span>

<span id="_Toc456790901" class="anchor"></span>

<span id="_Toc456790902" class="anchor"></span>

<span id="_Toc456790903" class="anchor"></span>

Reconnection DUT and Source devices after valid disconnection
-------------------------------------------------------------

+--------------------------------------+--------------------------------------+
| **\                                  | **Reconnection between Source**      |
| Test ID:**                           | **and DUT after valid disconnection  |
|                                      | **                                   |
+======================================+======================================+
| **Priority:**                        | **High Priority**                    |
+--------------------------------------+--------------------------------------+
| **Purpose:**                         | **To test: Ability of DUT reconnect  |
|                                      | after valid disconnection.**         |
+--------------------------------------+--------------------------------------+
| **Relevant OS:**                     | **Android**                          |
+--------------------------------------+--------------------------------------+
| **DUT Transmitter/Sink: **           | **Sink side**                        |
+--------------------------------------+--------------------------------------+
| **Preconditions:**                   | -   **HDCP Source** **& Sink** **is  |
|                                      |     installed, provisioned and       |
|                                      |     configured as HDCP 2.2 Dongle    |
|                                      |     connected to TV.**               |
|                                      |                                      |
|                                      | -   **Sink device connected to TV or |
|                                      |     monitor using HDMI cable.**      |
|                                      |                                      |
|                                      | -   **DUT & Source device in same    |
|                                      |     WI-FI network**                  |
+--------------------------------------+--------------------------------------+
| **Relevant source side devices:**    | **MediaTek k55v1\_64\_tee; Qualcomm  |
|                                      | MSM8996 (HLOS android); Qualcomm     |
|                                      | MSM8996 (HLOS windows)**             |
+--------------------------------------+--------------------------------------+

  **1.**   ***Connect devices via WFD/Projects***                             ***Connection established: Have mirroring between Trx & TV ***
  -------- ------------------------------------------------------------------ -------------------------------------------------------------------------------------------------------------------
  **2.**   ***Twist the device***                                             ***Devices stay connected: Have mirroring between Trx & TV***
  **3.**   ***Attempt to play any content (for e.g. from YouTube) ***         ***Smoothly playback: Have mirroring between Trx & TV***
  **4.**   ***Disconnect the Devices (by tap “end of connection” button)***   ***Devices disconnected: Mirroring between Trx & TV stopped***
  **5.**   ***Connect devices via WFD/Projects***                             ***Connection established: Have mirroring between Trx & TV ***
  **6.**   ***Twist the device***                                             ***Devices stay connected: Have mirroring between Trx & TV***
  **7.**   ***Disconnect the Devices (by tap*** ***end of connection)***      ***Devices disconnected: Mirroring between Trx & TV stopped***
  **8.**   ***Repeat steps 1-7*** ***on several occasions***                  ***Everything is performed with no issues***
  **9.**   ***Check in logcat (for android device)***:                        ***This logs do include messages: DX\_HDCP\_CONNECTION\_STATE\_AUTHENTICATED; DX\_HDCP\_CIPHER\_DATA succeeded***

<span id="_Toc456790905" class="anchor"></span>

<span id="_Toc456790906" class="anchor"></span>

<span id="_Toc456790907" class="anchor"></span>

<span id="_Toc456790908" class="anchor"></span>

<span id="_Toc456790909" class="anchor"></span>

<span id="_Toc456790910" class="anchor"></span>

<span id="_Toc456790911" class="anchor"></span>

<span id="_Toc456790912" class="anchor"></span>

<span id="_Toc456790913" class="anchor"></span>

<span id="_Toc456790914" class="anchor"></span>

Reconnection DUT and Source devices after non-valid disconnection
-----------------------------------------------------------------

+--------------------------------------+--------------------------------------+
| **\                                  | **Reconnection between Source**      |
| Test ID:**                           | **and DUT after non-valid            |
|                                      | disconnection **                     |
+======================================+======================================+
| **Priority:**                        | **High Priority**                    |
+--------------------------------------+--------------------------------------+
| **Purpose:**                         | **to test: Ability of DUT reconnect  |
|                                      | after non-valid disconnection.**     |
+--------------------------------------+--------------------------------------+
| **Relevant OS: **                    | **Android**                          |
+--------------------------------------+--------------------------------------+
| **DUT Transmitter/Sink: **           | **Sink side**                        |
+--------------------------------------+--------------------------------------+
| **Preconditions:**                   | -   **HDCP Source** **& Sink** **is  |
|                                      |     installed, provisioned and       |
|                                      |     configured as HDCP 2.2 Dongle    |
|                                      |     connected to TV.**               |
|                                      |                                      |
|                                      | -   **Sink device connected to TV or |
|                                      |     monitor using HDMI cable.**      |
|                                      |                                      |
|                                      | -   **DUT & Source device in same    |
|                                      |     WI-FI network**                  |
+--------------------------------------+--------------------------------------+
| **Relevant source side devices:**    | **MediaTek k55v1\_64\_tee; Qualcomm  |
|                                      | MSM8996 (HLOS android); Qualcomm     |
|                                      | MSM8996 (HLOS windows)**             |
+--------------------------------------+--------------------------------------+

  ---------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------
  **1.**   ***Connect devices via WFD/Projects***                                                         ***Connection established: Have mirroring between Trx & TV ***
  -------- ---------------------------------------------------------------------------------------------- -------------------------------------------------------------------------------------------------------------------
  **2.**   ***Twist the device***                                                                         ***Devices stay connected: Have mirroring between Trx & TV***

  **3.**   ***Attempt to play any content (for e.g. from YouTube) ***                                     ***Smoothly playback: Have mirroring between Trx & TV***

  **4.**   ***Disconnect the Trx and Sink*** ***(by pooling out cable or dongle from HDMI connector)***   ***Devices disconnected: Mirroring between Trx &* *TV stopped***
                                                                                                          
                                                                                                          ***On DUT: error message ***

  **5.**   ***Connect devices via WFD/Projects***                                                         ***Connection established: Have mirroring between Trx & TV ***

  **6.**   ***Twist the device***                                                                         ***Devices stay connected: Have mirroring between Trx & TV***

  **7.**   ***Disconnect the Devices (by stopping application)***                                         ***Devices disconnected: Mirroring between Trx & TV stopped***

  **8.**   ***Repeat steps 1-8 on several occasions***                                                    ***Everything is performed with no issues***

  **9.**   ***Check in logcat (for android device)***:                                                    ***This logs do include messages: DX\_HDCP\_CONNECTION\_STATE\_AUTHENTICATED; DX\_HDCP\_CIPHER\_DATA succeeded***
  ---------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------

**Behavior of HDCP connection after update version (with stored km)**
---------------------------------------------------------------------

+--------------------------------------+--------------------------------------+
| **\                                  | **Connection between Source** **and  |
| Test ID:**                           | DUT after update (with stored km) ** |
+======================================+======================================+
| **Priority:**                        | **High Priority**                    |
+--------------------------------------+--------------------------------------+
| **Purpose:**                         | **to test: Success of HDCP           |
|                                      | connection after update to HDCP new  |
|                                      | version (used before) **             |
+--------------------------------------+--------------------------------------+
| **Relevant OS: **                    | **Android**                          |
+--------------------------------------+--------------------------------------+
| **DUT Transmitter/Sink: **           | **Sink side**                        |
+--------------------------------------+--------------------------------------+
| **Preconditions:**                   | -   **HDCP Source** **& Sink** **is  |
|                                      |     installed, provisioned and       |
|                                      |     configured as HDCP 2.2 Dongle    |
|                                      |     connected to TV.**               |
|                                      |                                      |
|                                      | -   **Sink device connected to TV or |
|                                      |     monitor using HDMI cable.**      |
|                                      |                                      |
|                                      | -   **DUT & Source device in same    |
|                                      |     WI-FI network**                  |
+--------------------------------------+--------------------------------------+
| **Relevant source side devices:**    | **MediaTek k55v1\_64\_tee; Qualcomm  |
|                                      | MSM8996 (HLOS android); Qualcomm     |
|                                      | MSM8996 (HLOS windows)**             |
+--------------------------------------+--------------------------------------+

  **1.**   ***Execute provisioning on DUT with previous version of HDCP***                            ***DUT is provisioned ***
  -------- ------------------------------------------------------------------------------------------ --------------------------------------------------------------------------------------------------------------------
  **2.**   ***Connect devices via WFD/Projects***                                                     ***Connection established with no errors, have mirroring between Trx & TV***
  **3.**   ***Disconnect the Devices (by tap “end of connection” button)***                           ***Devices disconnected***
  **4.**   ***Install on DUT the current version: Trust Zone (test release); hlos (test release)***   ***DUT ready for E2E ***
  **5.**   ***Connect devices via WFD/Projects***                                                     ***Connection established with no errors, have mirroring between Trx & TV***
  **6.**   ***Disconnect the Devices (by tap “end of connection” button)***                           ***Devices disconnected***
  **7.**   ***Check in logcat (for android device)***:                                                ***This logs do include messages: DX\_HDCP\_CONNECTION\_STATE\_AUTHENTICATED; DX\_HDCP\_CIPHER\_DATA succeeded ***

Behavior of HDCP connection after update version (with no stored km)
--------------------------------------------------------------------

+--------------------------------------+--------------------------------------+
| **\                                  | **Connection between Source and DUT  |
| Test ID:**                           | after update to new version (no      |
|                                      | stored km)**                         |
+======================================+======================================+
| **Priority:**                        | **High Priority**                    |
+--------------------------------------+--------------------------------------+
| **Purpose:**                         | **to test: Success of HDCP           |
|                                      | connection after update to new HDCP  |
|                                      | version (no used before) **          |
+--------------------------------------+--------------------------------------+
| **Relevant OS: **                    | **Android**                          |
+--------------------------------------+--------------------------------------+
| **DUT Transmitter/Sink: **           | **Sink side**                        |
+--------------------------------------+--------------------------------------+
| **Preconditions:**                   | -   **HDCP Source & Sink is          |
|                                      |     installed, provisioned and       |
|                                      |     configured as HDCP 2.2 Dongle    |
|                                      |     connected to TV.**               |
|                                      |                                      |
|                                      | -   **Sink device connected to TV or |
|                                      |     monitor using HDMI cable.**      |
|                                      |                                      |
|                                      | -   **DUT & Source device in same    |
|                                      |     WI-FI network**                  |
+--------------------------------------+--------------------------------------+
| **Relevant source side devices:**    | **MediaTek k55v1\_64\_tee; Qualcomm  |
|                                      | MSM8996 (HLOS android); Qualcomm     |
|                                      | MSM8996 (HLOS windows)**             |
+--------------------------------------+--------------------------------------+

  **1.**   ***Execute provisioning on DUT ***                                                         ***DUT is provisioned***
  -------- ------------------------------------------------------------------------------------------ --------------------------------------------------------------------------------------------------------------------
  **2.**   ***Install on DUT the current version: Trust Zone (test release); hlos (test release)***   ***DUT ready for E2E ***
  **3.**   ***Connect devices via WFD/Projects***                                                     ***Connection established with no errors, have mirroring between Trx & TV***
  **4.**   ***Disconnect the Devices (by type end of connection)***                                   ***Devices disconnected***
  **5.**   ***Check in logcat (for android device)***:                                                ***This logs do include messages: DX\_HDCP\_CONNECTION\_STATE\_AUTHENTICATED; DX\_HDCP\_CIPHER\_DATA succeeded ***

<span id="_Toc456790918" class="anchor"></span>

<span id="_Toc456790919" class="anchor"></span>

<span id="_Toc456790920" class="anchor"></span>

<span id="_Toc456790921" class="anchor"></span>

<span id="_Toc456790922" class="anchor"></span>

<span id="_Toc456790923" class="anchor"></span>

<span id="_Toc456790924" class="anchor"></span>

<span id="_Toc456790925" class="anchor"></span>

<span id="_Toc456790926" class="anchor"></span>

Trobleshooting
==============

1.  If have connection (have mirroring between source & sink) but can’t
    establish HDCP connection, check if doesn’t have mismatch versions
    keys/lib/TZ application.

2.  Some times than can’t establish HDCP connection, may need to delete
    SFS file, make reboot and renew Provisioning.

3.  If DUT with production TZ app connected with production device and
    have HDCP authenticated on TV will appear black screen.

4.  If can’t found logs on Windows DUT ensure, that in DxHDCP.cfg
    have for.eg. LogPath=\\data\\HdcpLogs, if LogPath= a default path
    it’s a current directory not will write in (for.eg. \\data\\bin\\).

5.  MediaTek device may have DRM process running not rooted, before
    beginning E2E tests and after Provisioning will need to perform:

adb shell chown -R system:drmrpc /persist/data/
