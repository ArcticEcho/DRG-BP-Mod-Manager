# Mod Loader V3

The V3 mod loader provides a platform for mod developers to get their BluePrint mods loaded into the game. The loader requires mod files to be uniquely named following a set style `ModXXX`, where `XXX` is the mod ID, a number starting from 001 and currently ranging to 050 (including the prefixed 0s).

## Mod IDs

To avoid conflicts when building a new mod, simply pick the smallest unclaimed ID.

Claimed mod IDs:
 Mod ID | Mod Name | Author 
 -------|----------|-------
 001 | Advanced Darkness | ArcticEcho
 002 | Environmentalist | ArcticEcho
 003 | Mission Control Text Remover | ArcticEcho
 004 | Better Salvage Bar | ArcticEcho
 005 | Twitch Integration | TheMedicKnight
 006 | Minehead Gravity | ArcticEcho
 007 | MollyFixer  | TheMedicKnight
 008 | Garden Of Karl | GoldBl4d3
 009 | Enemy Spawner | GoldBl4d3
 010 | Twitch Integration System | GoldBl4d3
 011 | Mission Timer | ArcticEcho
 012 | Custom Waves | ArcticEcho
 013 | Object Debugger | ArcticEcho
 
 If you'd like to reservse/claim an ID please submit a [new ID claim](https://github.com/ArcticEcho/DRG-Mod-Loader/issues/new?assignees=ArcticEcho&labels=ID+Claim&template=id-claim.md&title=ID+Claim) or hit me up on discord.


# How To use

## Installation

Simply drop the [mod loader pak file](https://github.com/ArcticEcho/DRG-Mod-Loader/blob/master/FSD-WindowsNoEditor__ModLoaderV3P4.pak) into `C:\Program Files (x86)\Steam\steamapps\common\Deep Rock Galactic\FSD\Content\Paks` and you're ready to go.

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
