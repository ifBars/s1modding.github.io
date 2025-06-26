---
weight: 22300
title: "Accessing and Reading Game Code"
description: "Reading and understanding the game code for modding Schedule I"
icon: "code"
date: "2025-06-26T16:55:15+02:00"
lastmod: "2025-06-26T16:55:15+02:00"
draft: false
toc: true
---

Being able to read and understand the game's code is crucial for modding.

Thankfully, Schedule I is not obfuscated, which means you can easily read the code and understand how the game works. This is a great advantage for modders, as it allows you to create more complex and interesting mods.

## Decompiling the Game Code

**Switch branch to Mono** in Steam. This is necessary because IL2CPP code is compiled to C++ and then to machine code, which is much harder to read and understand. Mono, on the other hand, uses C# code that can be easily decompiled.

**Locate `Assembly-CSharp.dll`** in the game directory, which is usually located at `<game dir>\Schedule I_Data\Managed`.

You can **use a decompiler**, like [ILSpy](https://github.com/icsharpcode/ILSpy), [dnSpy](https://github.com/dnSpy/dnSpy) or [dotPeek](https://www.jetbrains.com/decompiler/), to decompile the code. These tools will allow you to view the C# code in a readable format.

If you're using ILSpy, you can simply drag and drop the `Assembly-CSharp.dll` file into the ILSpy window. This will load the assembly and allow you to browse the code. You also can right-click on the assembly and select "Save Code" to save the decompiled code to a folder. This way you can easily search through the code using your favorite text editor or IDE.

Feel free to explore the code and see how the game works. You can look at the classes, methods, and properties to understand how the game is structured. This will help you create mods that fit well with the game's design and functionality.

If you want to access some functionality, but you're unsure where to look for, you can use the search feature in your decompiler/IDE to find specific classes or methods. For example, if you want to find the code related to the player's inventory, you can search for "Inventory" or "PlayerInventory" in the decompiler.
