---
weight: 22200
title: "Creating Your First Mod"
description: "Making a basic MelonLoader mod"
icon: "start"
date: "2025-06-26T22:58:35+02:00"
lastmod: "2025-06-26T22:58:35+02:00"
draft: false
toc: true
---

In this guide, we will walk through the process of creating a basic MelonLoader mod for Schedule I. This mod will simply print a message to the console when the game starts.

This guide assumes you have already installed MelonLoader and set up your development environment. If you haven't done that yet, please refer to the [Environment Setup](/docs/moddevs/environment_setup/) guide.

## Your First Mod
To start off, we will be working in Mono backend, as it is easier to set up. This example will work with IL2CPP as well, but in larger projects, working with IL2CPP can be more complex.
```csharp
using MelonLoader;

[assembly: MelonInfo( typeof(MyMod.MyMod), "MyMod", "1.0.0", "YourName")]
[assembly: MelonGame("TVGS", "Schedule I")]

namespace MyMod
{
    public class MyMod : MelonMod
    {
        public override void OnInitializeMelon()
        {
            LoggerInstance.Msg("Hello, Schedule I!");
        }
    }
}
```

Build your project and place the resulting `.dll` file (in `bin/<config name>/<target framework>/MyMod.dll`) in the `Mods` folder of your Schedule I installation directory. The `Mods` folder is located at `<game dir>/Mods`.

When you start the game, you should see your mod in the list of loaded mods in the MelonLoader console, and the message "Hello, Schedule I!" should be printed to the console.

**Congratulations!** You've just created your first MelonLoader mod for Schedule I. This is a simple example, but it serves as a foundation for more complex mods.

## Next Steps
Now that you have a basic understanding of how to create a mod, you can start exploring the game's code and adding more functionality to your mod. You can access various game systems, modify existing behavior, and create new features.

MelonLoader provides a wide range of hooks and events that you can use to interact with the game. You can find more information about these in the [MelonLoader documentation](https://melonwiki.xyz/#/modders/quickstart).
