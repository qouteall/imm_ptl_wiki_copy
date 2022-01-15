
This wiki describes the latest version of Immersive Portals Mod Fabric version.

Mod download from CurseForge: https://www.curseforge.com/minecraft/mc-mods/immersive-portals-mod

Modrinth: https://modrinth.com/mod/immersiveportals

Discord server: https://discord.gg/BZxgURK

#### Common Questions

##### Can I use it in multiplayer?

Yes. The server and client must both install this mod. (This mod is not a plugin and cannot be used on bukkit or spigot.)

##### Sodium Compatibility?

In MC 1.18.1, the latest version of ImmPtl is roughly compatible with Sodium 0.4.0-alpha6.

In MC 1.17.1, the latest version of ImmPtl is roughly compatible with Sodium 0.3.3.

In 1.16.5 you can use [this](https://github.com/qouteall/sodium-fabric/releases).

##### Will the portal impact performance?

Yes. (Especially with dimension stack and scaled-view-type end portal.)

You can use Sodium (but not all Sodium versions are compatible with ImmPtl, see the above).

##### Which mods are incompatible with ImmPtl?

[Known compatibility issues](https://github.com/qouteall/ImmersivePortalsMod/issues?q=is%3Aissue+is%3Aopen+label%3A%22Mod+Compatibility%22).

##### How to integrate with other mod's portals?

You can use [datapack](https://github.com/qouteall/ImmersivePortalsMod/wiki/Datapack-Based-Custom-Portal-Generation#convert_vanilla_nether_portaljson-convent-vanilla-nether-portals-into-see-through-portals-if-the-shapes-are-compatible) to make it convert other mod's portals into see-through portals.

##### How to make portal helper craft-able in survival?

[Check this](https://github.com/qouteall/ImmersivePortalsMod/wiki/Portal-Customization#how-to-use-similar-functionality-in-survival-mode)

##### The nether portal is not see-through

This mod does not change existing vanilla portals. You need to light new portals.

##### The nether portal does not link

It can only link to an empty obsidian frame with the same shape and orientation (unless you change the nether portal mode in  the config).

#### How to install Immersive Portals Mod (Fabric version)

Immersive Portals works on Minecraft Java Edition, and does not work on Bedrock edition.

Firstly you need to install Fabric loader. (Check this https://fabricmc.net/wiki/install ). Download the Fabric loader installer here: https://fabricmc.net/use/ . Then open the Fabric loader installer to install Fabric loader.

After installing the Fabric loader, you need to download Fabric API (https://github.com/FabricMC/fabric/releases ). Fabric API is a mod. Fabric API is not Fabric loader.

And then [download Immersive Portals mod](https://qouteall.fun/immptl). You now get two jar files. Put these two jar files into `mods` folder. (You don't need to open these two jar files.) The `mods` folder is in the game directory. You can open the game directory from the launcher. If `mods` folder does not exist, create it. (launching MC with Fabric once will create the `mods` folder)

Note that you need to download the corresponding mod jar for the corresponding Minecraft version.

It's recommended to use Pehkui mod with this mod. Pehkui provides entity scaling functionality. Pehkui: https://www.curseforge.com/minecraft/mc-mods/pehkui (Currently this mod does not have integration with Pehkui on Forge.)

