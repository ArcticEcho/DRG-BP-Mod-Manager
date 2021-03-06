# BP Mod Manager

The mod manager provides a platform for mod developers to get their BluePrint mods loaded into the game, and lets users interact with them via an in-game GUI. The manager requires mod files to be placed in the `Content/_ModBPs` folder in your UE project, following a set naming style: `ModXXX`, where `XXX` is the mod ID (a number starting from 001 and currently ranging to 100, including the prefixed 0s).

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
 006 | MINE - Minehead Is Now Epic | ArcticEcho
 007 | MollyFixer  | TheMedicKnight
 008 | Garden Of Karl | GoldBl4d3
 009 | Enemy Spawner | GoldBl4d3
 010 | Twitch Integration System | GoldBl4d3
 011 | Mission Timer | ArcticEcho
 013 | Object Inspector | ArcticEcho
 014 | Better Post Processing | ArcticEcho
 015 | GoldBl4d3's Audio Suite | GoldBl4d3
 016 | Disco | ArcticEcho
 017 | Custom Enemy Cap | ArcticEcho
 018 | Dynamic Resolution | ArcticEcho
 019 | Time Control | ArcticEcho
 020 | Speed HUD | Bebe
 021 | Creator Menu | GoldBl4d3
 022 | Heart of Hoxxes | GoldBl4d3
 023 | Take Me Home | ArcticEcho
 024 | Custom Waves | ArcticEcho
 025 | Better Spectator | ArcticEcho
 026 | Generous Management | ArcticEcho
 027 | Spicy Balls | ArcticEcho
 028 | Hazard Infinity | GoldBl4d3
 029 | Homing Hell | GoldBl4d3
 030 | Fabulous Bugs | ArcticEcho
 031 | Mission Control | GoldBl4d3
 032 | Creator Platform | GoldBl4d3
 033 | Closer Promotion Terminal | ArcticEcho
 034 | Support Pods | Our Lord And Savior Gabe Newell
 035 | Upgraded Doretta | Our Lord And Savior Gabe Newell
 036 | RabidScotsmanMod | GoldBl4d3
 037 | Panini FOV | ArcticEcho
 038 | Seasonal Space Rig | Our Lord And Savior Gabe Newell
 039 | Equipment Changer | Our Lord And Savior Gabe Newell
 040 | Let There Be Light | Our Lord And Savior Gabe Newell
 041 | Fabulous Molly | ArcticEcho
 042 | ReloadBar | Samamstar
 043 | Patcifist Mode | Our Lord And Savior Gabe Newell
 044 | Mother Of All Blimps | ArcticEcho
 045 | Teleport Players | Our Lord And Savior Gabe Newell
 046 | Motion Radar | GoldBl4d3
 047 | Minimap | GoldBl4d3
 049 | Prop Pack | Pacagma and Samamstar
 050 | Custom action bindings | Samamstar
 051 | Maxwell's Demon | Darth Pointer
 052 | Berzerker Plus | Darth Pointer
 066 | Better Time Control | Buckminsterfullerene
 067 | IYDRASYACH | Buckminsterfullerene
 068 | Force Takeoff | Buckminsterfullerene
 069 | DJDwarves | Buckminsterfullerene

 
 If you'd like to reservse/claim an ID please submit a [new ID claim](https://github.com/ArcticEcho/DRG-Mod-Loader/issues/new?assignees=ArcticEcho&labels=ID+Claim&template=id-claim.md&title=ID+Claim) or hit me up on discord.


# How To use

## Installation

Simply download mod manager pak file and move it into `C:\Program Files (x86)\Steam\steamapps\common\Deep Rock Galactic\FSD\Content\Paks`.

## Creating a new mod

 - 1: In your Unreal Engine project, create a folder named `_ModBPs` in your content folder. Your content browser should look like this:
 
 ![](https://i.imgur.com/PaG745W.png)

 - 2: Download the ModBase BluePrint and place it in `_ModBPs`.
 
 - 3: Create a new BP in `_ModBPs` with `ModBase` as the parent class, and name the file `ModXXX` (replacing `XXX` with your mod ID):
 
 ![](https://i.imgur.com/5RtGtcM.png)
 
 - 4: In your new BP, go to the class defaults and set your mod name, author, and version.
 
 ![](https://i.imgur.com/woJnLN8.png)
 
 - 5: From the event BeginPlay, bind to the `OnInitialise` event and get your mod ready for use (initialise UI, load save data, etc.). If you're embedding your UI, set the `ModUI` variable after you've created your widget. Do **not** start your mod from this event.
 
 ![](https://i.imgur.com/5IWdC0T.png)
 
 - 6: Bind to the `OnStart` event and create the necessary logic to enable/start your mod.
 
 ![](https://i.imgur.com/mGCEqUB.png)
 
 - 7: Bind to the `OnStop` event and create the necessary logic to disable/stop your mod.
 
 ![](https://i.imgur.com/cBsGznq.png)
 
If you're embedding your UI, you may find the `OnUIOpened` and `OnUIClosed` events helpful for carrying out additional tasks (for example, initialising slider values when the UI opens, or saving data when the UI closes).

If you still need help feel free to submit an issue.
