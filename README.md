# BP Mod Manager

The [BP mod manager](https://drg.mod.io/bpmm) provides a central UI for interacting/configuring BP mods, you can open up the menu with the default keybinding `N`.

# Quick Start Guide For Mod Devs

If you'd like to integrate your BP mod into the manager, simply follow the steps below depending on the loading system you plan on using.

## Native Loading System

Assuming you've followed all the steps to get your BP mod ready for native loading:

 - 1: [Download](https://github.com/ArcticEcho/DRG-BP-Mod-Manager/raw/master/IManagedMod.uasset) the IManagedMod BP interface and add it to your project.

 - 2: Add the interface to your mod's main BP:

![image](https://user-images.githubusercontent.com/4972533/131170252-5dcda850-673a-4ccd-a3a2-468b706dbb29.png)

 - 3: Expand the "Interfaces" tab, open the `GetConfig` function, and implement it (fill out the mod name, author, etc. fields and make sure to pass your mod config UI).

![image](https://user-images.githubusercontent.com/4972533/131170780-760220ae-0bd0-4acf-8e6f-bc26f87822dc.png)

 - 4 (**optional**): If you plan on supporting on-the-fly mod enable/disable toggling, make sure the "Can Be Toggled Off" option is checked, and implement the Handle Enable Event/Handle Disable Event (right click on the event in the interfaces tab, and select "Implement Function").
 
 ![image](https://user-images.githubusercontent.com/4972533/131171139-5cd2d789-1445-4492-a926-1b6ca4b6e13a.png)



## Alternate Loading System

The manager provides an alternate loading system, where supported mods will be loaded in faster than the native BP spawning system. (Mods are spawned when the player controller is fully initialised on level load, i.e., almost immediately after entering a level). Your BP mod must be placed in the `Content/_ModBPs` folder in your UE project. The file must follow a set naming format: `ModXXX`, where `XXX` is your mod's ID (a number between 001 and 150, including the prefixed 0s).

### Claimed ALS Mod IDs
 
 To avoid conflicts, we keep track of claimed ALS IDs. If you're making a new mod that targets this system, please submit an [ID claim](https://github.com/ArcticEcho/DRG-Mod-Loader/issues/new?assignees=ArcticEcho&labels=ID+Claim&template=id-claim.md&title=ID+Claim) (or hit me up on discord).

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
 055 | Random Mission Selection | Darth Pointer
 066 | Better Time Control | Buckminsterfullerene
 067 | IYDRASYACH | Buckminsterfullerene
 068 | Force Takeoff | Buckminsterfullerene
 069 | DJDwarves | Buckminsterfullerene
 070 | Deep Coaster Tycoon | Our Lord And Savior Gabe Newell
 071 | Upgraded Molly | Our Lord And Savior Gabe Newell
 072 | Swarm Size Control | NaturalBornCamper
 073 | HazardPersistanceEnjoyer | Darth Pointer
 074 | Display Events | HandDrawnNerd

### Creating a new ALS mod

 - 1: In your Unreal Engine project, create a folder named `_ModBPs` in your content folder. Your content browser should look like this:
 
 ![](https://i.imgur.com/PaG745W.png)

 - 2: [Download](https://github.com/ArcticEcho/DRG-BP-Mod-Manager/raw/master/ModBaseV2.uasset) the `ModBaseV2` BP and add it to your project.
 
 - 3: Create a new BP in `_ModBPs` with `ModBaseV2` as the parent class, and name the file `ModXXX` (replacing `XXX` with your mod ID):
 
 ![](https://i.imgur.com/5RtGtcM.png)
 
 - 4: In your new BP, go to the class defaults and set your mod name, author, and version.
 
 ![](https://i.imgur.com/woJnLN8.png)
 
 - 5: From the `BeginPlay` event get your mod ready for use: initialise UI, load save data, etc. Make sure to set the `ModUI` variable after you've created your widget. Do **not** start your mod from this event, use the `OnStart` event instead.
 
 - 6: Bind to the `OnStart` event and create the necessary logic to enable/start your mod.
 
 ![](https://i.imgur.com/mGCEqUB.png)
 
 - 7: Bind to the `OnStop` event and create the necessary logic to disable/stop your mod.
 
 ![](https://i.imgur.com/cBsGznq.png)
 

If you still need help feel free to submit an issue.
