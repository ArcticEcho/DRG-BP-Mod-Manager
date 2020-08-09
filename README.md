# Mod Loader V3

![](https://cdn.discordapp.com/attachments/732650220214681600/742014938561642639/unknown.png)

The V3 mod loader provides a platform for mod developers to get their BluePrint mods loaded into the game. The loader requires mod files to be uniquely named follwoing a set style `ModXXX`, where `XXX` is the mod ID, a number starting from 001 (and currently ranging to 050).

To avoid conflicts, simply pick the smallest unclaimed ID.

Claimed mod IDs:
 Mod ID | Mod Name | Author 
 -------|----------|-------
 001 | Advanced Darkness | ArcticEcho
 002 | Environmentalist | ArcticEcho
 003 | Mission Control Text Remover | ArcticEcho
 004 | Better Salvage Bar | Arctic Echo
 005 | Twitch Integration | TheMedicKnight
 
 If you'd like to reservse/claim an ID please submit a [new ID claim](https://github.com/ArcticEcho/DRG-Mod-Loader/issues/new?assignees=ArcticEcho&labels=ID+Claim&template=id-claim.md&title=ID+Claim).


# How To use

## Installation

Simply drop the [mod loader pak file](https://github.com/ArcticEcho/DRG-Mod-Loader/blob/master/FSD-WindowsNoEditor__ModLoaderV3.pak) into `C:\Program Files (x86)\Steam\steamapps\common\Deep Rock Galactic\FSD\Content\Paks` and you're ready to go.

## Creating a new mod

 - 1: In your Unreal Engine project, create a folder named `_ModBPs` in your content folder. Your content browser should look like this:
 
 ![](https://i.imgur.com/PaG745W.png)

 - 2: Download the [ModBase](https://github.com/ArcticEcho/DRG-Mod-Loader/blob/master/ModBase.uasset) file and place it in `_ModBPs`.
 
 - 3: Create a new BP in `_ModBPs` with `ModBase` as the parent class, and name the file `ModXXX` (replacing `XXX` with your mod ID):
 
 ![](https://i.imgur.com/5RtGtcM.png)
 
 - 4: In your new BP, from the `BeginPlay` event, set the `ModName`, `ModVersion`, and `ModAuthor` variables.
 
 ![](https://i.imgur.com/sXUyeqY.png)
 
 - 5: Bind to the `OnInitialise` event and get your mod ready for use (initialise UI, load save data, etc.). If you're embedding your UI, set the `ModUI` variable after you've created your widget. Do **not** start your mod from this event.
 
 ![](https://i.imgur.com/5IWdC0T.png)
 
 - 6: Bind to the `OnStart` event and create the necessary logic to enable/start your mod.
 
 ![](https://i.imgur.com/mGCEqUB.png)
 
 - 7: Bind to the `OnStop` event and create the necessary logic to disable/stop your mod.
 
 ![](https://i.imgur.com/cBsGznq.png)
 
If you're embedding your UI, you may find the `OnUIOpened` and `OnUIClosed` events helpful for carrying out additional tasks (for example, initialising slider values when the UI opens, or saving data when the UI closes).

Check out the [wiki](https://github.com/ArcticEcho/DRG-Mod-Loader/wiki) for more info. If you still need help feel free to submit an issue.
