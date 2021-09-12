# CARLA

## Preparation

Make sure you have installed [Unreal Engine](../unreal-engine) and everything in [dependencies](../dependencies). 

Then open a powershell, cmd, or Windows Terminal to proceed.  

### Clone the Repository

You can clone the latest release of CARLA by

```bash
git clone https://github.com/carla-simulator/carla
```

The repository is quite small, and it doesn't take much time to clone it.

!!! Important

    Do not use "Download zip" on GitHub to download CARLA. You need a repo clone since it use git tags to provide version information for the Makefile.

??? Note "Previous CARLA versions"

     The `master` branch contains the current release of CARLA with the latest fixes and features. Previous CARLA versions are tagged with the version name. Always remember to check the current branch in git with the command `git branch`.

### Download Assets

Download the latest assets to work with the current version of CARLA by running the following command in the CARLA root folder:

```bash
Update.bat
```

The size of the assets file is around 10-15 GB, which may takes a long time to download if you have a poor internet connection to the AWS Cloud. The assets will be downloaded and extracted to the appropriate location if 7zip is installed.

### Set Unreal Engine Environment Variable

It is necessary to set an environment variable so that CARLA can find the Unreal Engine installation folder. To set the environment variable:

1. Open Windows Control Panel and go to `Advanced System Settings` or search for `Advanced System Settings` in the Windows search bar.
2. On the `Advanced` panel open `Environment Variables...`.
3. Click `New...` to create the variable.
4. Name the variable `UE4_ROOT` and choose the path to the installation folder of the desired Unreal Engine installation.


## Build

All commands in this stage should be executed via the `x64 Native Tools Command Prompt for VS 2019`. Open this by clicking the Windows key and searching for x64. All commands should be run in the root CARLA folder.

### PythonAPI

The Python API client grants control over the simulation. Compilation of the Python API client is required the first time you build CARLA and again after you perform any updates.

```bash
make PythonAPI
```

The compilation will take about 15-20 minutes on a desktop with a 24-core CPU, or about 1-2 hours on a laptop. Please br patient if you don't have a powerful CPU.

After the compilation, a `.whl` file will be generated. You can install it with
```bash
pip3 install <path/to/wheel>.whl
```


??? Warning "Multiple CARLA versions"

    Issues can arise through the use of different methods to install the CARLA client library and having different versions of CARLA on your system. It is recommended to use virtual environments when installing the `.whl` and to uninstall any previously installed client libraries before installing new ones.


### CarlaUE4Editor

The following command compiles and launches Carla Unreal Engine Editor. Run this command each time you want to launch the server or use the Carla Unreal Engine Editor:

```bash
make launch
```

The compilation will take about 10-15 minutes on a desktop with a 24-core CPU. Be patient again.

After the compilation, the Carla Unreal Engine Editor will be launched. 

!!! Important
    
    If it is the first time you launch it, there will possible be a pop up and ask you to "locate main renderdoc executable". It seems that if you fail to locate it, the  UE4Editor will crash before loading. You can find the renderdoc executable in `C:\Program Files\RenderDoc\`.
