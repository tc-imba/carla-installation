# Dependencies

## List of Dependencies

### Visual Studio 2019

Get the 2019 version of Visual Studio from [here](https://developerinsider.co/download-visual-studio-2019-web-installer-iso-community-professional-enterprise/). Choose __Community__ for the free version. Use the _Visual Studio Installer_ to install three additional elements: 

* __Windows 8.1 SDK.__ Select it in the _Installation details_ section on the right or go to the _Indivdual Components_ tab and look under the _SDKs, libraries, and frameworks_ heading.
* __x64 Visual C++ Toolset.__ In the _Workloads_ section, choose __Desktop development with C++__. This will enable a x64 command prompt that will be used for the build. Check that it has been installed correctly by pressing the `Windows` button and searching for `x64`. Be careful __not to open a `x86_x64` prompt__.  
* __.NET framework 4.6.2__. In the _Workloads_ section, choose __.NET desktop development__ and then in the _Installation details_ panel on the right, select `.NET Framework 4.6.2 development tools`. This is required to build Unreal Engine. 


!!!Important

    Other Visual Studio versions may cause conflict. Even if these have been uninstalled, some registers may persist. To completely clean Visual Studio from the computer, go to `Program Files (x86)\Microsoft Visual Studio\Installer\resources\app\layout` and run `.\InstallCleanup.exe -full`  

### Software Dependencies

* [__CMake__](https://cmake.org/download/) generates standard build files from simple configuration files.  
* [__Git__](https://git-scm.com/downloads) is a version control system to manage CARLA repositories.  
* [__Make__](http://gnuwin32.sourceforge.net/packages/make.htm) generates the executables. It is necessary to use __Make version 3.81__, otherwise the build may fail. If you have multiple versions of Make installed, check that you are using version 3.81 in your PATH when building CARLA. You can check your default version of Make by running `make --version`.
* [__7Zip__](https://www.7-zip.org/) is a file compression software. This is required for automatic decompression of asset files and prevents errors during build time due to large files being extracted incorrectly or partially.
* [__Python3 x64__](https://www.python.org/downloads/) is the main scripting language in CARLA. Having a x32 version installed may cause conflict, so it is highly advisable to have it uninstalled.
* [__RenderDoc__](https://renderdoc.org/) is a standalone open-source graphics debugger that you can use to perform single-frame captures and inspect them.

### Python Dependencies

You should install Python3 before this step. pip version 20.3 is required. In a fresh setup, this requirement should be met directly. 

You can run the following commands to ensure everything is set up in Python.

```sh
pip3 install --upgrade pip
pip3 install --user setuptools
pip3 install --user wheel
```


## Install Dependencies By Package Manager (Chocolatey)

> There are a lot of different installer formats and multiple approaches 
> to deploying Windows software. Deploying software without package management 
> on Windows can be complicated and time-consuming. 
> 
> -- [Chocolatey Documentation: Why Chocolatey?](https://chocolatey.org/why-chocolatey)

That's why we recommend to use `Chocolatey` to install all dependencies on Windows.

### Install Chocolatey

First, ensure that you are using an administrative powershell. You can open it by `Win+X` and selecting "Windows Powershell (Admin)" in Windows 7,8,10 or "Windows Terminal (Admin)" in Windows 11.

Then, enter the following command:

```powershell
Set-ExecutionPolicy Bypass -Scope Process -Force; [System.Net.ServicePointManager]::SecurityProtocol = [System.Net.ServicePointManager]::SecurityProtocol -bor 3072; iex ((New-Object System.Net.WebClient).DownloadString('https://community.chocolatey.org/install.ps1'))
```

If you don't see any errors, you are ready to use Chocolatey! Type `choco` or `choco -?` now to see the help message. Check more details on https://chocolatey.org/install.

### Install Dependencies

The installation command is quite straight-forward, very similar to those package managers on Linux. You only need to wait a few minutes until all dependencies are installed.

```sh
choco install -y cmake git make 7zip python renderdoc
```

Check the dependencies by

```sh
git --version
make -v
python --version
pip3 --version
```

!!! Note
    
    By default, `cmake` is not automatically added to the `PATH`. You can add it if you need to run it in command line (not required since Visual Studio 2019 also ships a builtin cmake in x64 Visual C++ Toolset). `renderdoc` is not a command line tool so it is not checked here as well.

## Install Dependencies Manually

Really want to do it manually? Try to install the dependencies one by on by downloading the setup file on their websites. Maybe there will be a guide **a few moments later**.
