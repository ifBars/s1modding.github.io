---
weight: 22600
title: "Patching"
description: "Patch game code to modify or extend functionality"
icon: "syringe"
date: "2025-06-27T00:27:24+02:00"
lastmod: "2025-06-27T00:27:24+02:00"
draft: false
toc: true
---

Patching is a powerful feature, allowing you to modify or extend the functionality of the game code without directly altering the original files.

## What is Patching?
Patching allows you to inject your own code into the game's execution flow. This can be used to modify existing methods, add new functionality, or even replace entire methods.

## How to Patch
### Automatic Patching
We let MelonLoader handle the patching process automatically. When you build your mod, MelonLoader will automatically apply your patches to the game code when the game starts.
To patch a method, you need to use `Harmony`, a library which ships with MelonLoader. Here's a basic example of how to patch a method:
```csharp
using HarmonyLib;
using MelonLoader;

[HarmonyPatch(typeof(TargetClass), "TargetMethod")]
public class MyPatch
{
    public static void Prefix()
    {
        // Code to run before the original method
    }

    public static void Postfix()
    {
        // Code to run after the original method
    }
}
```

In this example, `TargetClass` is the class containing the method you want to patch, and `TargetMethod` is the method you want to modify. The `Prefix` method runs before the original method, and the `Postfix` method runs after it. `Prefix` and `Postfix` methods must be static.

You can also use Harmony to act on the instance, change the return value, or stop the original method from executing.
```csharp
[HarmonyPatch(typeof(TargetClass), "TargetMethod")]
public class MyPatch
{
    public static bool Prefix(TargetClass __instance, ref int __result)
    {
        // Modify the result before the original method runs
        __result = 42; // Change the return value to 42
        
        // Return false to skip the original method
        return false; 
    }
}
```
Other parameters passed to the method also can be used and could be required to be listed in the patch method signature.
```csharp
class TargetClass
{
    public bool DoubleIt;
    public bool ShouldDouble()
    {
        return DoubleIt;
    }
    public int TargetMethod(int input)
    {
        if (ShouldDouble())
        {
            return input * 2; // Original method
        }
        return input; // Original method
    }
}

[HarmonyPatch(typeof(TargetClass), "TargetMethod")]
public class MyPatch
{
    public static bool Postfix(TargetClass __instance, int input, ref int __result)
    {
        // Modify the result after the original method runs
        if (__instance.ShouldDouble())
        {
            __result = input * 3; // Change the return value to input * 3 if ShouldDouble() is true
            return false; // Skip the original method
        }
        // If ShouldDouble() is false, let the original method run
        return true; // Continue with the original method
    }
}
```
Additionally, you can use `HarmonyTranspiler` to modify the IL code of the method directly, allowing for more complex modifications.

The important thing to remember about Transpilers, is that they modify the IL code, and thus, will not work on IL2CPP builds, as they are compiled to C++ and then to machine code. Transpilers are only available for Mono builds.

### Patching manually
If you want to patch manually, you can use `HarmonyInstance`.
```csharp
using HarmonyLib;
using MelonLoader;

[HarmonyDontPatchAll] // From MelonLoader - prevents automatic patching of all methods in this class
public class MyMod : MelonMod
{
    HarmonyInstance harmony;
    public override void OnInitializeMelon()
    {
        harmony = this.HarmonyInstance;
        harmony.PatchAll(); // but we do it anyway, manually
    }
}
```
To actually patch a specific method, when you want to (not necessarily at the start of the game), you can use:
```csharp
MethodInfo privateMethod = typeof(TargetClass).GetMethod("TargetMethod", new Type [] { typeof(int) });

// We pass in the method we want to patch, the prefix method, the postfix method, and the finalizer method
harmony.Patch(privateMethod, new HarmonyMethod(typeof(MyPatch), "PatchMethodName"), null, null);
```


## Resources
- [Harmony Documentation](https://harmony.pardeike.net/articles/patching.html)
