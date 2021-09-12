# Unreal Engine

Starting with version 0.9.12, CARLA uses a modified fork of Unreal Engine 4.26. This fork contains patches specific to CARLA.


## Register and Link GitHub Account and Unreal Engine's Account

Be aware that to download this fork of Unreal Engine, __you need to have a GitHub account linked to Unreal Engine's account__. If you don't have this set up, please follow [this guide](https://www.unrealengine.com/en-US/ue4-on-github) before going any further.

Following is a summary of the guide.

### GitHub Account

Ensure you have a [GitHub](https://github.com) account before processing.

### Epic Game Account

Ensure you have an [Epic Game](https://accounts.unrealengine.com/) account before processing.

### Link Accounts

1. Open your Epic Game account dashboard, hover over your username, and select the Personal button from the drop-down menu.
2. With your account dashboard open, select the Connections tab from the sidebar. 
3. After opening the Connections menu, select the Accounts tab, and then select the Connect button below the GitHub icon.
4. Select the Unreal Engine End User License Agreement (EULA) appropriate for your needs and read through the terms, then select the Link Account button. 
5. To complete the OAuth App Authorization process, click the Authorize EpicGames button.
6. GitHub will send an email inviting you to join the @EpicGames organization on GitHub. You must select the Join @EpicGames button in this email within seven days to complete the GitHub and Epic Games account linking process. 
7. Upon completion, you will receive an email from Epic Games verifying that your GitHub and Epic Games accounts were successfully linked. 

## Build Unreal Engine

To build the modified version of Unreal Engine:

### Clone

In a terminal, navigate to the location you want to save Unreal Engine and clone the _carla_ branch:

```sh
git clone --depth 1 -b carla https://github.com/CarlaUnreal/UnrealEngine.git
cd UnrealEngine
```

!!! Note

    Keep the Unreal Engine folder as close as `C:\\` as you can because if the path exceeds a certain length (usually 128) then `Setup.bat` will return errors in step 3.

### Setup 

Run the configuration scripts:

```sh
Setup.bat
GenerateProjectFiles.bat
```

### Compile

Compile the modified engine:

1. Open the `UE4.sln` file inside the source folder with Visual Studio 2019.

2. In the build bar ensure that you have selected 'Development Editor', 'Win64' and 'UnrealBuildTool' options. Check [this guide](https://docs.unrealengine.com/en-US/ProductionPipelines/DevelopmentSetup/BuildingUnrealEngine/index.html) if you need any help. 
        
3. In the solution explorer, right-click `UE4` and select `Build`.

### Validation

Once the solution is compiled you can open the engine to check that everything was installed correctly by launching the executable `Engine\Binaries\Win64\UE4Editor.exe`.

!!! Note
    If the installation was successful, this should be recognised by Unreal Engine's version selector. You can check this by right-clicking on any `.uproject` file and selecting `Switch Unreal Engine version`. You should see a pop-up showing `Source Build at PATH` where PATH is the installation path that you have chosen. If you can not see this selector or the `Generate Visual Studio project files` when you right-click on `.uproject` files, something went wrong with the Unreal Engine installation and you will likely need to reinstall it correctly.

!!! Important
    A lot has happened so far. It is highly advisable to restart the computer before continuing.