---
weight: 22100
title: "Getting Started"
description: "Setting up your modding environment for Schedule I"
icon: "rocket_launch"
date: "2025-06-26T16:51:26+02:00"
lastmod: "2025-06-26T16:51:26+02:00"
draft: false
toc: true
---

To start off, you need to set up your modding environment. This guide will help you install the necessary tools and get started with modding Schedule I.

## Prerequisites
- A copy of Schedule I installed via Steam.
- Familiarity with basic programming concepts and C#.
- A code editor or IDE (e.g., Visual Studio, Visual Studio Code, Rider).
- Basic understanding of Unity and MelonLoader.

Install MelonLoader and be sure to read through [Mod Users](/docs/modusers/) section to familiarize yourself with the modding ecosystem.

Install .NET SDK 6.0 or later. You can use newer versions, like [10.0](https://dotnet.microsoft.com/en-us/download/dotnet/10.0), allowing you to use the latest C# features.

## Setting up your development environment

**Install a Code Editor or IDE**
- Download and install [Rider](https://www.jetbrains.com/rider/) or [Visual Studio](https://visualstudio.microsoft.com/).
- If you prefer a lightweight option, you can use [Visual Studio Code](https://code.visualstudio.com/) with extensions.

### Seting up your project
#### Templates
There's an assortment of templates available for quickly starting your modding project.
- [MelonLoader Mod Template](https://github.com/TrevTV/MelonLoader.VSWizard/releases) - Official MelonLoader template for Visual Studio.
- [Mono Mod Template for MelonLoader and BepInEx](https://github.com/MaxtorCoder/ScheduleOnePluginTemplate) - Customizable template for creating mods with Mono and MelonLoader or BepInEx. Includes optional support for Unity scripts projects to create asset bundles. By [MaxtorCoder](https://github.com/MaxtorCoder).
- [Basic modding template for Mono](https://github.com/XOWithSauce/schedule-mono-example) - A simple template for creating mods with Mono. By [XOWithSauce](https://github.com/XOWithSauce).
- [Basic modding template for IL2CPP](https://github.com/XOWithSauce/schedule-il2cpp-example) - A simple template for creating mods with IL2CPP. By [XOWithSauce](https://github.com/XOWithSauce).
- [S1 Mono+IL2CPP C# Project Template](https://github.com/weedeej/S1MONO_IL2CPP_Template) - Clean template with conditional compilation for Mono and IL2CPP. Includes AssetBundleUtils for loading asset bundles. By [weedeej](https://github.com/weedeej).
- [Yet Another MelonMod Template with batteries included](https://github.com/k073l/S1MelonModTemplate) - Template featuring cross-backend (IL2CPP and Mono) compatibility, easy build and test process, automatic loading of testing mods, and more. By [k073l](https://github.com/k073l).

#### Manual Setup
If you prefer to set up your project manually, follow these steps:
1. Create a new C# Class Library project in your IDE. Be sure to target:
    - For Mono: .NETStandard 2.1
    - For IL2CPP: .NET 6.0
2. Include references to files you'll need:
    - `MelonLoader.dll` (from `MelonLoader/net35` or `MelonLoader/net6` folder in your game directory, depending on your target backend)
    - `UnityEngine.dll` (from `<game dir>/Schedule I_Data/Managed` or `MelonLoader\Il2CppAssemblies\` for IL2CPP)
    - `Assembly-CSharp.dll` (from `<game dir>/Schedule I_Data/Managed` or `MelonLoader\Il2CppAssemblies\` for IL2CPP)
    - other references as needed
3. If you are using Mono, you can also add a NuGet package - [BepInEx Publicizer](https://www.nuget.org/packages/BepInEx.AssemblyPublicizer.MSBuild). Then, when you include `Assembly-CSharp.dll` in your project, add
```xml
<Reference Include="Assembly-CSharp" Publicize="true">
    <Private>false</Private>
    <HintPath><game dir>\Schedule I_Data\Managed\Assembly-CSharp.dll</HintPath>
</Reference>
```
to publicize the types in `Assembly-CSharp.dll`. This will allow you to access private and protected members, without the need to use reflection.

You're now free to start coding your mod by creating a class that inherits from `MelonMod`.

Further information can be found in [Creating Your First Mod](/docs/moddevs/creating_your_first_mod/) guide.

## Additional Resources
- [MelonLoader Documentation](https://melonwiki.xyz/)
- [Unity Documentation](https://docs.unity3d.com/2022.3/Documentation/Manual/index.html)
- [C# Programming Guide](https://docs.microsoft.com/en-us/dotnet/csharp/)
- [Schedule I Modding Discord](https://discord.gg/9Z5RKEYSzq)
