---
weight: 22250
title: "Publishing"
description: "Publishing your mod on modding platforms"
icon: "conveyor_belt"
date: "2025-06-28T01:52:53+02:00"
lastmod: "2025-06-28T01:52:53+02:00"
draft: false
toc: true
---

You've created a mod and now you want to share it with others. This guide will help you understand how to publish your mod on Thunderstore and Nexus Mods, the two main platforms for Schedule I mods.

## Thunderstore
[Thunderstore](https://thunderstore.io/c/schedule-i/) is a popular modding platform, featuring an open-source approach.

You'll need to create an account on Thunderstore or use social login options like Discord or GitHub. Then, you'll need to create your [team](https://thunderstore.io/settings/teams/create/).

### Creating a Mod Package
To publish your mod, you need to create a [mod package](https://thunderstore.io/package/create/docs/). This is a ZIP file that contains your mod's DLL file, README and other metadata required by Thunderstore.

**Files to include in the package:**
- Your mod's DLL file (e.g., `MyMod.dll`). Can be in the root of the package or in a `Mods` folder.
- `README.md` file with information about your mod, installation instructions, and usage. This file is important as it will be displayed on your mod's page.
- `icon.png` file, must be 256x256 resolution and a PNG. This will be displayed on the mod's page and in the mod list.
- `CHANGELOG.md` (optional) file with a list of changes in each version of your mod. Will be displayed on the mod's page.
- `LICENSE.md` (optional) file with the license for your mod. You can use a license like MIT, GPL, or any other license you prefer. This is important to clarify the terms under which your mod can be used and distributed. Check out [ChooseALicense.com](https://choosealicense.com/) or [TL;DR Legal](https://tldrlegal.com/) for more information on licenses.
- `manifest.json` file with metadata about your mod. This file is required by Thunderstore and should contain the following information:
```json
{
    "name": "My_Mod", // The name of your mod. Underscores are replaced with spaces in the mod list.
    "version_number": "1.0.0", // The version of your mod, following semantic versioning (MAJOR.MINOR.PATCH). You will need to bump this version number, if you want to update your mod listing.
    "website_url": "", // Optional: URL to your mod's website or GitHub repository
    "description": "A brief description of my mod", // A short description of your mod, displayed on the mod list and mod page
    "dependencies": [ // List of dependencies your mod requires to work. Check out dependency strings on mod pages on Thunderstore to see how they look like.
        "LavaGang-MelonLoader-0.7.0", // Required dependency for MelonLoader mods
        "the_croods-SwapperPlugin-1.2.2" // Optional: SwapperPlugin can be used if you have 2 .DLLs - Mono and IL2CPP. This helps mod loaders to load the correct version of your mod based on the game branch.
    ]
}
```
[Markdown Cheatsheet](https://www.markdownguide.org/cheat-sheet/) can help you format your `.md` files.

[Manifest Validator](https://thunderstore.io/tools/manifest-v1-validator/) can help you validate your `manifest.json` file.

Zip all these files into a single ZIP file. Files should be in the root of the ZIP file, not in a subfolder.

### Uploading the Mod Package
1. Go to [Upload Mod](https://thunderstore.io/c/schedule-i/create/) page.
2. Select your team from the dropdown menu.
3. Upload the ZIP file you created earlier.
4. In Communities, select "Schedule I" to publish your mod in the Schedule I community.
5. Select applicable categories for your mod. If it's a mod, select "Mod", if it .DLL for Mono, select "Mono", same for IL2CPP.
6. If your mod is NSFW, select "NSFW" checkbox.
7. Submit the form.
8. If everything is correct, your mod will be published and available for download on Thunderstore.

*Note:* Uploaded packages can't be deleted, but can be deprecated, which will hide the package. To fully remove a mod, you need to contact Thunderstore staff.

## Nexus Mods
[Nexus Mods](https://www.nexusmods.com/games/schedule1) is another popular mod platform, containing a large number of mods for various games, including Schedule I.
Nexus guide will be shorter, as the mod submission form takes you through the process step by step and doesn't require you to create a package.

To publish your mod on Nexus Mods, you'll need to create an account.

Click Upload button in the top right corner of the page, then select "Mod" as the type of your upload.

### Uploading the Mod
Select the game you want to upload the mod for, in this case, Schedule I.

Fill in all necessary information about your mod. NexusMods requires you to provide a title, description, and other metadata about your mod. You can also upload images and videos to showcase your mod.

#### Mod Files
In Manage Files section, you can upload your mod files. You can upload a ZIP file containing your mod's DLL file. Prefer to upload a ZIP file with only 1 `.dll` file in it and describe the branch in the filename and/or description. You can upload multiple files, so you have a version for Mono and IL2CPP, if you want to support both branches.

### Finishing
Click the button in "Publish mod" section to publish your mod. Your mod will be automatically scanned for viruses and other issues. If everything is correct, your mod will be published and available for download on Nexus Mods.
