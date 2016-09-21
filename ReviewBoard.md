<div id="header">

<div>

Search:

</div>

<div id="logo">

[![MoinMoin Logo](/moin_static194/common/moinmoin.png)](/FrontPage)

</div>

<span id="pagelocation"><span class="pagepath">[CP](/CP)<span class="sep">/</span>[PRODUCTS](/CP/PRODUCTS)<span class="sep">/</span>[HA](/CP/PRODUCTS/HA)<span class="sep">/</span>[TOOLS](/CP/PRODUCTS/HA/TOOLS){.nonexistent}</span><span class="sep">/</span>[ReviewBoard](/CP/PRODUCTS/HA/TOOLS/ReviewBoard?action=fullsearch&value=linkto%3A%22CP%2FPRODUCTS%2FHA%2FTOOLS%2FReviewBoard%22&context=180 "Click to do a full-text search for this title"){.backlink}</span> {#locationline}
==============================================================================================================================================================================================================================================================================================================================================================================================================================================================================

-   [RecentChanges](/RecentChanges)
-   [FindPage](/FindPage)
-   [HelpContents](/HelpContents)
-   [ReviewBoard](/CP/PRODUCTS/HA/TOOLS/ReviewBoard)

<div id="pageline">

------------------------------------------------------------------------

</div>

</div>

<div id="page" lang="en" dir="ltr">

<div id="content" dir="ltr" lang="en">

<span id="top" class="anchor"></span> <span id="line-1"
class="anchor"></span>

ReviewBoard {#ReviewBoard}
===========

<span id="line-2" class="anchor"></span><span id="line-3"
class="anchor"></span>

<div class="table-of-contents">

Contents

1.  [ReviewBoard](#ReviewBoard)
    1.  [Installing RB tools](#Installing_RB_tools)
    2.  [Windows Command line setup](#Windows_Command_line_setup)
    3.  [Linux/OSX Command line setup](#Linux.2FOSX_Command_line_setup)
    4.  [Troubleshooting](#Troubleshooting)

</div>

<span id="line-4" class="anchor"></span><span id="line-5"
class="anchor"></span>
Review Board is a tool for reviewing source code, documentation and
other text-based files. It offers a powerful web-based interface with
broad browser support for managing review requests and reviewing code,
as well as command line tools to simplify the review request submission
process. <span id="line-6" class="anchor"></span><span id="line-7"
class="anchor"></span>

<span id="line-8" class="anchor"></span><span id="line-9"
class="anchor"></span>

<div class="important">

<span id="line-1-1" class="anchor"></span>
To setup an account just login to the [Discretix ReviewBoard
server](http://reviewboard.discretix.com){.http} with your network user
and password

</div>

<span id="line-10" class="anchor"></span><span id="line-11"
class="anchor"></span>

Installing RB tools {#Installing_RB_tools}
-------------------

<span id="line-12" class="anchor"></span>
RB tools is a python based command line utility. Please read the ["rbt
post"](http://www.reviewboard.org/docs/rbtools/){.http} documentation.
<span id="line-13" class="anchor"></span>The currently known good
version is 0.7.4 . <span id="line-14" class="anchor"></span><span
id="line-15" class="anchor"></span>

Windows Command line setup {#Windows_Command_line_setup}
--------------------------

<span id="line-16" class="anchor"></span>
RBTools requires Python, easy\_install and a diff utility on the PATH.
Python directories must be present on the PATH. <span id="line-17"
class="anchor"></span><span id="line-18" class="anchor"></span>

<span id="line-19" class="anchor"></span><span id="line-20"
class="anchor"></span>

<div class="important">

<span id="line-1-2" class="anchor"></span>
Having Python(x, y) installed is the fastest and easiest way to get
RBtools up and running.

</div>

<span id="line-21" class="anchor"></span><span id="line-22"
class="anchor"></span>
Details: <span id="line-23" class="anchor"></span>

-   If python is NOT installed install Python(x, y): <span id="line-24"
    class="anchor"></span>
    -   [Python](file:///Y:/CP/HWA/WindowsBlue/Tools/Python(x,y)-2.7.10.0.exe){.file} -
        `Y:/CP/HWA/WindowsBlue/Tools/Python(x,y)-2.7.10.0.exe`{.backtick}
        <span id="line-25" class="anchor"></span>
    -   Install for "All Users" <span id="line-26"
        class="anchor"></span>
    -   Select FULL Install Configuration <span id="line-27"
        class="anchor"></span>
    -   Use default destination directories. <span id="line-28"
        class="anchor"></span>
-   If python installed and is NOT Python(x, y): <span id="line-29"
    class="anchor"></span>
    -   Add the following directories to the PATH if not there already:
        <span id="line-30" class="anchor"></span>
        -   `c:\Python27`{.backtick} <span id="line-31"
            class="anchor"></span>
        -   `c:\Python27\Scripts`{.backtick} <span id="line-32"
            class="anchor"></span>
        -   `c:\Python27\DLLs`{.backtick} <span id="line-33"
            class="anchor"></span>
    -   Install
        [setuptools](https://pypi.python.org/pypi/setuptools#installation-instructions){.https}
        <span id="line-34" class="anchor"></span>
    -   OR uninstall and install Python(x, y) <span id="line-35"
        class="anchor"></span>
-   install RBtools from a command line by executing: <span id="line-36"
    class="anchor"></span><span id="line-37" class="anchor"></span><span
    id="line-1-3" class="anchor"></span>

    <div class="highlight bat">

    <div class="codearea" dir="ltr" lang="en">

    ``` {#CA-5f209cf0072b155c8a3ef0254f6947643393a45f dir="ltr" lang="en"}
    pip install -U rbtools
    ```

    </div>

    </div>

    <span id="line-38" class="anchor"></span>

    Expected Output: <span id="line-39" class="anchor"></span><span
    id="line-40" class="anchor"></span><span id="line-41"
    class="anchor"></span><span id="line-42" class="anchor"></span><span
    id="line-43" class="anchor"></span><span id="line-44"
    class="anchor"></span><span id="line-45" class="anchor"></span><span
    id="line-46" class="anchor"></span><span id="line-47"
    class="anchor"></span><span id="line-48" class="anchor"></span><span
    id="line-49" class="anchor"></span><span id="line-50"
    class="anchor"></span><span id="line-51" class="anchor"></span><span
    id="line-52" class="anchor"></span><span id="line-53"
    class="anchor"></span><span id="line-54" class="anchor"></span><span
    id="line-1-5" class="anchor"></span>

    <div class="highlight bat">

    <div class="codearea" dir="ltr" lang="en">

    ``` {#CA-7eb83460c405639e319ce829a098b8ec5394067a dir="ltr" lang="en"}
       1 C:\>easy_install -U rbtools
       2 Searching for rbtools
       3 Reading https://pypi.python.org/simple/rbtools/
       4 ...
       5 Adding RBTools 0.7.4 to easy-install.pth file
       6 Installing post-review-script.py script to C:\Python27\Scripts
       7 Installing post-review.exe script to C:\Python27\Scripts
       8 Installing post-review.exe.manifest script to C:\Python27\Scripts
       9 Installing rbt-script.py script to C:\Python27\Scripts
      10 Installing rbt.exe script to C:\Python27\Scripts
      11 Installing rbt.exe.manifest script to C:\Python27\Scripts
      12 
      13 Installed c:\python27\lib\site-packages\rbtools-0.7.4-py2.7.egg
      14 Processing dependencies for rbtools
      15 Finished processing dependencies for rbtools
    ```

    </div>

    </div>

    <span id="line-55" class="anchor"></span><span id="line-56"
    class="anchor"></span>

-   Check for ``{.backtick}diff``{.backtick} command line utility on the
    path: <span id="line-57" class="anchor"></span><span id="line-58"
    class="anchor"></span><span id="line-1-7" class="anchor"></span>

    <div class="highlight bat">

    <div class="codearea" dir="ltr" lang="en">

    ``` {#CA-3195f45e789b1d1d4154ad77e4be5a3f3bf55b88 dir="ltr" lang="en"}
    where diff
    ```

    </div>

    </div>

    <span id="line-59" class="anchor"></span>

-   if no diff utility found: <span id="line-60" class="anchor"></span>
    -   Install [Chocolatey](http://chocolatey.org){.http} by opening an
        administrative `cmd.exe`{.backtick} and running the command:
        <span id="line-61" class="anchor"></span><span id="line-62"
        class="anchor"></span><span id="line-1-9" class="anchor"></span>

        <div class="highlight bat">

        <div class="codearea" dir="ltr" lang="en">

        ``` {#CA-a702ed9d23e3bdfd642a6415206b22e2dabf4630 dir="ltr" lang="en"}
        @powershell -NoProfile -ExecutionPolicy Bypass -Command "iex ((new-object net.webclient).DownloadString('https://chocolatey.org/install.ps1'))" && SET PATH=%PATH%;%ALLUSERSPROFILE%\chocolatey\bin
        ```

        </div>

        </div>

        <span id="line-63" class="anchor"></span>

    -   Install [GOW](https://github.com/bmatzelle/gow/wiki){.https}
        <span id="line-64" class="anchor"></span><span id="line-65"
        class="anchor"></span><span id="line-1-11"
        class="anchor"></span>

        <div class="highlight bat">

        <div class="codearea" dir="ltr" lang="en">

        ``` {#CA-608e74f4a9b7aec6bd99e195ab4c1ac374711f8b dir="ltr" lang="en"}
        cinst Gow
        ```

        </div>

        </div>

        <span id="line-66" class="anchor"></span>

    -   reboot <span id="line-67" class="anchor"></span>

<span id="line-68" class="anchor"></span><span id="line-69"
class="anchor"></span>

<div class="note">

<span id="line-1-13" class="anchor"></span>
There are many alternative ways to get diff for windows - whatever works
for you.

</div>

<span id="line-70" class="anchor"></span><span id="line-71"
class="anchor"></span>

Linux/OSX Command line setup {#Linux.2FOSX_Command_line_setup}
----------------------------

<span id="line-72" class="anchor"></span><span id="line-73"
class="anchor"></span>
-   Uninstall system pip if installed <span id="line-74"
    class="anchor"></span><span id="line-75" class="anchor"></span><span
    id="line-1-14" class="anchor"></span>

    <div class="highlight bash">

    <div class="codearea" dir="ltr" lang="en">

    ``` {#CA-c4b5e27f0a727a9ef90286c71a8b11b8a9408ea0 dir="ltr" lang="en"}
    sudo apt-get purge python-pip
    ```

    </div>

    </div>

    <span id="line-76" class="anchor"></span>

-   Install pip <span id="line-77" class="anchor"></span><span
    id="line-78" class="anchor"></span><span id="line-1-16"
    class="anchor"></span>

    <div class="highlight bash">

    <div class="codearea" dir="ltr" lang="en">

    ``` {#CA-81ddc85668b4c9b876b8cf8e386de68defd548e3 dir="ltr" lang="en"}
    curl https://raw.github.com/pypa/pip/master/contrib/get-pip.py | sudo python
    ```

    </div>

    </div>

    <span id="line-79" class="anchor"></span>

-   install RBtools <span id="line-80" class="anchor"></span><span
    id="line-81" class="anchor"></span><span id="line-1-18"
    class="anchor"></span>

    <div class="highlight bash">

    <div class="codearea" dir="ltr" lang="en">

    ``` {#CA-0cc9416a6348ec7800f5d8d577ae33bbb4928f20 dir="ltr" lang="en"}
    sudo -H pip install -U rbtools
    ```

    </div>

    </div>

    <span id="line-82" class="anchor"></span>

-   Check RBtools <span id="line-83" class="anchor"></span><span
    id="line-84" class="anchor"></span><span id="line-85"
    class="anchor"></span><span id="line-86" class="anchor"></span><span
    id="line-87" class="anchor"></span><span id="line-1-20"
    class="anchor"></span>

    <div class="highlight console">

    <div class="codearea" dir="ltr" lang="en">

    ``` {#CA-eceed45ed0d3a06cc9b1e985305861ceaeb548e9 dir="ltr" lang="en"}
       1 $ rbt --version
       2 RBTools 0.7.5
       3 gabid@gabid-pcubu12 ~
       4 $
    ```

    </div>

    </div>

    <span id="line-88" class="anchor"></span><span id="line-89"
    class="anchor"></span>

Troubleshooting {#Troubleshooting}
---------------

<span id="line-90" class="anchor"></span>
-   Q: Executing `rbg post`{.backtick} on windows command line results
    fails with the error:
    `CRITICAL: environment can only contain string`{.backtick}. <span
    id="line-91" class="anchor"></span>

    -   A: update rbtools to at least 0.7.5
        (`pip install -U rbtools`{.backtick}). <span id="line-92"
        class="anchor"></span>

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
