---
weight: 11200
title: "Installing Mods and Plugins"
description: "How to install mods and plugins for MelonLoader"
icon: "extension"
date: "2025-06-18T21:02:21+02:00"
lastmod: "2025-06-18T21:02:21+02:00"
draft: false
toc: true
---

If you have installed MelonLoader, you can now install mods and plugins for Schedule I.

## Important Notes

{{< alert context="warning" >}}
<b>Always back up</b> your game files and save files before installing mods or plugins. Mods can cause issues, and backups let you restore your game if needed.
{{< /alert >}}

{{< alert context="info" >}}
<b>Check mod compatibility</b> with your version of Schedule I. Some mods require specific game or MelonLoader versions.
{{< /alert >}}

{{< alert context="danger" >}}
<b>Beware of malicious mods.</b> Download mods from trusted sources. If you're unsure about the mod's safety, check the comments or reviews on the mod page, or ask in the community Discord server. There's also a scanner, developed by Bars available at <a href="https://thunderstore.io/c/schedule-i/p/ifBars/MLVScan/">MLVScan</a> that can help catch some suspicious mods. However, it is not a guarantee that the mod is safe, so always be cautious.
{{< /alert >}}

---

# Automatic Installation

Use a mod manager like [r2modman](https://thunderstore.io/c/schedule-i/p/ebkr/r2modman/) or [Gale](https://thunderstore.io/c/schedule-i/p/Kesomannen/GaleModManager/) for Thunderstore mods, or [Vortex](https://www.nexusmods.com/site/mods/1) for NexusMods mods. These mod managers will automatically handle installation of MelonLoader and mods.

# Manual Installation

If you prefer manual installation, follow these steps:

## Installing Mods

Check if the mod is compatible with your game branch. Many mods target the main branch; some require the alternate branch. If unsure, check the mod description or author. Explanation of branches can be found in the [Common Terms](/docs/modusers/common_terms/) guide.

Download the mod from trusted sources like [Thunderstore](https://thunderstore.io/c/schedule-i/) or [NexusMods](https://www.nexusmods.com/games/schedule1/mods).

Extract the downloaded archive. You should find a `.dll` file or a `Mods` folder containing `.dll` files. For multiple `.dll`s, see the [Common Terms](/docs/modusers/common_terms/) guide.

Copy the `.dll` file(s) into the `Mods` folder in your Schedule I game directory. Create the `Mods` folder if it doesn't exist.

## Installing Plugins

Plugins enhance MelonLoader features and are usually `.dll` files.

{{< alert context="warning" >}}
<b>Plugins are not mods and vice versa.</b> Confirm from the description if the file is a plugin.
{{< /alert >}}

Download the plugin from trusted sources.

Extract the archive if needed. Find the `.dll` file or a `Plugins` folder containing `.dll`s.

Copy the plugin `.dll` file(s) into the `Plugins` folder in your Schedule I game directory. Create the `Plugins` folder if missing.
