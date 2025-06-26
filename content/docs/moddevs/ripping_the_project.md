---
weight: 22400
title: "Opening the game in Unity Editor"
description: "Looking at the game in Unity Editor for modding Schedule I"
icon: "settings"
date: "2025-06-26T17:03:36+02:00"
lastmod: "2025-06-26T17:03:36+02:00"
draft: false
toc: true
---

Download the [Unity Editor](https://unity.com/download) and install it. Make sure to install the version that matches the one used by Schedule I, which is Unity 2022.3.32f1 (as of the time of writing).

## Ripping the Project
To open Schedule I in Unity Editor, you need to rip the project files from the game. This process involves extracting the necessary files from the game's data folder.

For that purpose, you can use a tool like [AssetRipper](https://github.com/AssetRipper/AssetRipper). AssetRipper allows you to extract the Unity project files from the game's data folder, which you can then open in Unity Editor.

1. **Download AssetRipper** from the [GitHub releases page](https://github.com/AssetRipper/AssetRipper/releases/latest) or from their Patreon page, if you want to use AssetRipper Premium and support the developers.
2. **Run AssetRipper** and select File > Open Folder. Navigate to the Schedule I game folder, which is usually located at `C:\Program Files (x86)\Steam\steamapps\common\Schedule I`.
3. Once you see a green "View Loaded Files" button, you can verify that AssetRipper has successfully loaded the game files.
4. Click Export > Export all files.
5. Choose a destination folder where you want to save the ripped project files.
6. Click Export Unity Project to export the project files. This may take some time.

Note: You might need to fix the shaders. You can do this using [Schedule One URP Shader Fix](https://github.com/xmusjackson/SIShaderFix).

## Without AssetRipper
If you don't want to use AssetRipper for a whole project, you can use [Unity Project for Schedule One](https://github.com/Skippeh/ScheduleOne_UnityProject).

Download the repository, open `Assets/Plugins/ScheduleOne` folder. Drag and drop `Managed` folder (can be found in `<game dir>/Schedule I_Data`) onto the `.bat` file.

Open the project in Unity Editor.