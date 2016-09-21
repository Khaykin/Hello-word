# ReviewBoard

##Contents

```
- ReviewBoard
- Installing RB tools
- Windows Command line setup
- Linux/OSX Command line setup
- Troubleshooting
```

- Review Board is a tool for reviewing source code, documentation and
  other text-based files. It offers a powerful web-based interface with
  broad browser support for managing review requests and reviewing code,
  as well as command line tools to simplify the review request submission
  process.
- To setup an account just login to the [Discretix ReviewBoard server](http://reviewboard.discretix.com) with your network user and password.

## Installing RB tools

- RB tools is a python based command line utility. Please read the ["rbt
post"](http://www.reviewboard.org/docs/rbtools/) documentation.
- The currently known good version is 0.7.4 . 

## Windows Command line setup

- RBTools requires Python, easy_install and a diff utility on the PATH.
- Python directories must be present on the PATH.
- Having Python(x, y) installed is the fastest and easiest way to get RBtools up and running.

- Details: 
  - If python is NOT installed install Python(x, y): [Python](\\qnap\shared\CP\HWA\WindowsBlue\Tools\Python(x,y)
  - Install for "All Users"
  - Select FULL Install Configuration
  - Use default destination directories. 
  - If python installed and is NOT Python(x, y): 
    -   Add the following directories to the PATH if not there already:
        -   `c:\Python27`
        -   `c:\Python27\Scripts`
        -   `c:\Python27\DLLs`
    - Install [setuptools](https://pypi.python.org/pypi/setuptools#installation-instructions)
    - OR uninstall and install Python(x, y)
  - install RBtools from a command line by executing:

    ```
    pip install -U rbtools
    ```

    Expected Output: 

    ``` 
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

  - Check for `diff` command line utility on the path: `where diff`
  
  - If no diff utility found: 
    - Install [Chocolatey](http://chocolatey.org) by opening an
        administrative `cmd.exe` and running the command:
       
    `@powershell -NoProfile -ExecutionPolicy Bypass -Command "iex ((new-object net.webclient).DownloadString('https://chocolatey.org/install.ps1'))" && SET PATH=%PATH%;%ALLUSERSPROFILE%\chocolatey\bin`
    -   Install [GOW](https://github.com/bmatzelle/gow/wiki) `cinst Gow`
    -   reboot 
    -   There are many alternative ways to get diff for windows - whatever works

## Linux/OSX Command line setup 

 - Uninstall system pip if installed: `sudo apt-get purge python-pip`
 - Install pip: `curl https://raw.github.com/pypa/pip/master/contrib/get-pip.py | sudo python`
 - install RBtools: `sudo -H pip install -U rbtool`s
 - Check RBtools: `rbt --version`
 ```
    rbt --version
    RBTools 0.7.5
    gabid@gabid-pcubu12 ~
    $
 ```

## Troubleshooting 
- Q: Executing `rbg post` on windows command line results fails with the error:
     `CRITICAL: environment can only contain string`
- A: update rbtools to at least 0.7.5
     `pip install -U rbtools`
