---
weight: 11100
title: "Installing MelonLoader"
description: "A guide on installing the mod loader"
icon: "download"
date: "2025-06-18T20:47:07+02:00"
lastmod: "2025-06-18T20:47:07+02:00"
draft: false
toc: true
---

MelonLoader is a mod loader for Unity games, including Schedule I.

Official MelonLoader documentation can be found on the [MelonWiki](https://melonwiki.xyz/). This is a simplified guide to installing MelonLoader for Schedule I.

## Installation Steps

### Automatic Installation

Install a mod manager like [r2modman](https://thunderstore.io/c/schedule-i/p/ebkr/r2modman/), [Gale](https://thunderstore.io/c/schedule-i/p/Kesomannen/GaleModManager/) for Thunderstore mods or [Vortex](https://www.nexusmods.com/site/mods/1) for NexusMods mods. These mod managers should automatically install MelonLoader for you when you install your first mod or ask you to install it, if they can't do that.

### Manual Installation
#### Windows

##### Installing pre-requisites
Following software is required to run MelonLoader:

[Microsoft Visual C++ 2015-2019 Redistributable 64 Bit](https://aka.ms/vs/16/release/vc_redist.x64.exe)

[.NET Desktop Runtime 6.0 64 Bit](https://dotnet.microsoft.com/en-us/download/dotnet/6.0#runtime-desktop-6.0.19)

##### Installing MelonLoader
Download [MelonLoader 0.7.0](https://github.com/LavaGang/MelonLoader/releases/download/v0.7.0/MelonLoader.Installer.exe) and run it.


The installer should automatically detect your Schedule I installation. If it does not, you can manually select the game folder.
Select the game folder of Schedule I, which is usually located at `C:\Program Files (x86)\Steam\steamapps\common\Schedule I`.

Click "Install" to install MelonLoader.

#### Linux
It is assumed that you have a working installation of Schedule I on Linux (using Proton). If you're using Wine, you can follow Windows steps or use `winetricks` in your Wine prefix to install the required dependencies.

###### Installing pre-requisites
Install [protontricks](https://github.com/Matoking/protontricks) for easy installation of the required dependencies.

This allows you to install .NET Desktop 6.0 automatically, via `protontricks 3164500 dotnetdesktop6`. You also might need to install the Visual C++ 2015-2019 Redistributable via `protontricks 3164500 vcrun2015`.

###### Installing MelonLoader
Download [MelonLoader 0.7.0](https://github.com/LavaGang/MelonLoader/releases/download/v0.7.0/MelonLoader.Installer.Linux) and run it.
Make sure to give it execute permissions with 
```bash
chmod +x MelonLoader.Installer.Linux
```

Follow the instructions on screen to install MelonLoader.

To make sure MelonLoader starts with the game, add `WINEDLLOVERRIDES="version=n,b" %command%` to the launch options of Schedule I in Steam. If you are using Wine, you can handle the override in `winecfg` for your Wine prefix.

#### MacOS
There are [reports](https://www.applegamingwiki.com/wiki/Schedule_I) of Schedule I running on MacOS using Wine, however I found the most success with running it with CrossOver.
Here, it will also be assumed that you have a working installation of Schedule I on MacOS (using Wine or CrossOver).

###### Installing pre-requisites
Install them in the same way as on Windows with CrossOver, or use `winetricks` in your Wine prefix to install the required dependencies.

###### Installing MelonLoader
Follow the same steps as on Windows.

You also need to make sure that the overrides are set in Steam launch options. Alternatively, you can set the overrides in your Wine prefix with `winecfg`, or click "Wine Configuration" in CrossOver and set the overrides in libraries.

## Running Schedule I with MelonLoader
Run the game through Steam as usual. First startup after installing MelonLoader or after updating the game may take a bit longer.

If you have installed MelonLoader correctly, the moment you start the game, a console window should appear. Once the MelonLoader initializes, the game window should open.
