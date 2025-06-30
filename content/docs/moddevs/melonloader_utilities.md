---
weight: 22500
title: "MelonLoader Utilities"
description: "Useful tools provided by MelonLoader"
icon: "hardware"
date: "2025-06-26T23:23:27+02:00"
lastmod: "2025-06-26T23:23:27+02:00"
draft: false
toc: true
---

{{< alert context="info" >}}
This is not an exhaustive list of all the tools provided by MelonLoader, but it should cover the most commonly used ones. For more information, refer to the <a href="https://melonwiki.xyz/#/modders/quickstart">MelonLoader documentation</a>.
{{< /alert >}}

- **MelonLogger**:
You can use `LoggerInstance` in non-static context of your mod class to log messages to the console. This is useful for debugging and providing feedback to the player.
If you want to log messages in static context, MelonLoader provides a singleton instance of your mod class that you can use to access the logger:
```csharp
Melon<MyMod>.LoggerInstance.Msg("This is a message from static context");
```
You also can use `.Error` or `.Warning` to log error or warning messages, respectively.

- Callbacks:
MelonLoader provides various callbacks that you can override in your mod class to execute code at specific points in the game lifecycle. For example, you can override `OnUpdate` to execute code every frame, or `OnSceneWasLoaded` to execute code when a new scene is loaded.
```csharp
public override void OnUpdate()
{
    // This code will be executed every frame
    LoggerInstance.Msg("Updating..."); // Don't do this - it will spam the console and lag a lot!
}
public override void OnSceneWasLoaded(int buildIndex, string sceneName)
{
    // This code will be executed when a new scene is loaded
    LoggerInstance.Msg($"Scene {sceneName} was loaded!");
    if (sceneName == "Main")
    {
        LoggerInstance.Msg("We're loading the game!");
    }
}
```

{{< alert context="warning" >}}
<b>Performance tip:</b> Don't log messages every frame in <code>OnUpdate</code> - it will spam the console and cause significant performance issues!
{{< /alert >}}

You can also subscribe to events, using `MelonEvents`:
```csharp
MelonEvents.OnUpdate.Subscribe(() =>
{
    // This code will be executed every frame
    Melon<MyMod>.LoggerInstance.Msg("Updating...");
}, 100); // The higher the number, the lower the priority.
```

- **MelonPreferences**:
MelonLoader provides a way to create preferences for your mod, which can be accessed and modified by the player in `UserData/MelonPreferences.cfg` or a custom file.

You can create preferences using the `MelonPreferences.CreateCategory` method, and then create preferences using `MelonPreferences.CreateEntry` method. Here's an example:
```csharp
private MelonPreferences_Category category;
private MelonPreferences_Entry<bool> entry1;

public override void OnInitializeMelon()
{
    category = MelonPreferences.CreateCategory("MyMod", "My Mod Preferences");
    entry1 = category.CreateEntry("EnableFeature", true, "Enable Feature", "This is a feature that can be enabled or disabled.");
}

public override void OnSceneWasLoaded(int buildIndex, string sceneName)
{
    if (entry1.Value)
    {
        LoggerInstance.Msg("Feature is enabled!");
    }
    else
    {
        LoggerInstance.Msg("Feature is disabled!");
    }
}
```

{{< alert context="success" >}}
MelonLoader automatically saves the preferences to the file when the game is closed, so you don't need to worry about saving them yourself.
{{< /alert >}}

You can also use `MelonPreferences.Save` to save the preferences manually, if you want to save them at a specific point in time.

If you want to create a custom preferences file, use:
```csharp
category.SetFilePath("Foo/Bar.cfg");
category.SaveToFile();
```

- **MelonEnvironment**:
Provides a way to access various paths related to the framework, such as the game directory, user data directory, and mod directory.

{{< alert context="primary" >}}
<code>MelonEnvironment.UserDataDirectory</code> is particularly useful for storing user data, such as preferences or mod-specific save data you don't want in game's save system.
{{< /alert >}}

- **MelonCoroutines**:
MelonLoader provides a way to create coroutines, which are methods that don't block the main thread and can be used to execute code over multiple frames. This is useful for tasks that take a long time to complete, such as loading assets or performing complex calculations.

You can create a coroutine using the `MelonCoroutines.Start` method, which takes a method that returns an `IEnumerator`. Here's an example:
```csharp
public override void OnSceneWasLoaded(int buildIndex, string sceneName)
{
    MelonCoroutines.Start(MyCoroutine());
}
private IEnumerator MyCoroutine()
{
    LoggerInstance.Msg("Starting coroutine...");
    yield return new WaitForSeconds(1f); // Wait for 1 second
    LoggerInstance.Msg("Coroutine finished!");
}
```
You can also use `MelonCoroutines.Stop` to stop a coroutine, if you need to.
```csharp
MelonCoroutines.Stop(MyCoroutine());
// or pass in the object returned by `MelonCoroutines.Start` to stop a specific coroutine
object coroutine = MelonCoroutines.Start(MyCoroutine());
MelonCoroutines.Stop(coroutine);
```