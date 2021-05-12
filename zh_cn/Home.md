
这是空间折叠(Immersive Portals)模组的说明书。其说明内容针对1.16版本对应的模组。

CurseForge: https://www.curseforge.com/minecraft/mc-mods/immersive-portals-mod

Discord server: https://discord.gg/BZxgURK

#### 常见问题{#Common Questions}

##### 是否可以在多人游戏中使用？{#Can I use it in multiplayer?}

是的。服务端与客户端都应装本模组。

##### 怎样在服务器中使用位面纵向堆叠？{#How to enable dimension stack on a server?}

先用客户端创建位面纵向堆叠的世界，再将存档复制到服务端上。


##### 怎样改变其他模组的传送门？{#How to integrate with other mod's portals?}

使用[数据包](https://github.com/qouteall/ImmersivePortalsMod/wiki/Datapack-Based-Custom-Portal-Generation#convert_vanilla_nether_portaljson-convent-vanilla-nether-portals-into-see-through-portals-if-the-shapes-are-compatible) 来实现转换其他模组的传送门。

##### 传送门是否会影响性能{#Will the portal impact performance?}

是的。(尤其是位面纵向堆叠与缩放式末地传送门)

如果你遇到卡顿，可以
* 调低渲染距离
* 开启 "限制性传送门渲染".
* 关闭 "完全加载仅传送门可视区块".

参见[设置选项](https://github.com/qouteall/ImmersivePortalsMod/wiki/Config-Options)

##### 怎样在生存模式中使用传送门辅助方块{#How to make portal helper craft-able in survival?}

[参见](https://github.com/qouteall/ImmersivePortalsMod/wiki/Portal-Customization#how-to-use-similar-functionality-in-survival-mode)

#### 怎样安装该模组{#How to install Immersive Portals Mod (Fabric version)}

本模组仅适用于Java版Minecraft，不适用于基岩版。

首先要安装Fabric加载器。 ( https://fabricmc.net/wiki/install)。 下载加载器的安装程序: https://fabricmc.net/use/  然后打开该程序，安装加载器。

安装完Fabric加载器后，需要安装Fabric API。 (https://github.com/FabricMC/fabric/releases) 。Fabric API是一个模组，不是Fabric加载器。

然后下载 [本模组](https://qouteall.fun/immptl)。现在你得到了两个jar文件，讲这两个jar文件放入 `mods` 文件夹。 (不用打开这两个jar文件。) `mods` 文件夹在游戏目录中。可以从启动器里打开游戏目录。若 `mods` 文件夹不存在，创建该文件夹。 (安装Fabric后正常启动游戏就会自动创建  `mods` 文件夹)

注意，不同的Minecraft版本需要不同的模组版本。

建议安装Pehkui模组。Pehkui提供让实体缩放的功能。Pehkui: https://www.curseforge.com/minecraft/mc-mods/pehkui