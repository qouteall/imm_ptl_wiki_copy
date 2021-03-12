## 全局传送门命令{#Global Portal Commands}

使用全局传送门命令需要2级权限。

#### `/portal global convert_global_portal_to_normal_portal`

只能由玩家使用。将玩家指向的全局传送门转换为普通传送门。要求玩家靠近传送门中心。

#### `/portal global convert_normal_portal_to_global_portal`

只能由玩家使用。将玩家指向的普通传送门转换为全局传送门。

#### `/portal global create_inward_wrapping <x1> <z1> <x2> <z2>`

创建内向空间自折叠。生成的传送门为全局传送门。两个XZ坐标代表空间自折叠区域，传送门在纵向从y=0处覆盖到y=256处。

#### `/portal global create_outward_wrapping <x1> <z1> <x2> <z2>`

与上一个类似，但创建外向空间自折叠。

#### `/portal global remove_wrapping_zone`

将玩家所在的全局传送门空间自折叠区域的传送门移除。不影响由普通传送门组成的空间自折叠。

#### `/portal global view_wrapping_zones`

显示目前位面的空间自折叠区域以及编号。

#### `/portal global remove_wrapping_zone <id>`

根据编号移除空间自折叠区域。

#### `/portal global connect_floor <dimensionA> <dimensionB>`

创建传送门从 `dimensionA` 的底部连接 `dimensionB` 的顶部。仅生成一个单向全局传送门。

#### `/portal global connect_ceil <dimensionA> <dimensionB>`

创建传送门从 `dimensionA` 的顶部连接 `dimensionB` 的底部。仅生成一个单向全局传送门。

#### `/portal global connection_remove_floor <dimension>`

移除该位面的底部的连接传送门。仅移除一个全局传送门。

#### `/portal global connection_remove_ceil <dimension>`

移除该位面的顶部的连接传送门。仅移除一个全局传送门。


## 针对传送门的命令{#Portal Targeted Commands}

创造模式玩家或2级权限所有者可以使用这些命令。

这些命令只针对一个传送门实体。若命令发送者为玩家，则针对的传送门为玩家看向的传送门。若命令发送者为传送门实体，则命令针对该传送门实体。

这些命令不针对全局传送门。

### 修改传送门的指向{#Change the Portal's Destination}

#### `/portal set_portal_destination <dimenision> <x> <y> <z>`

将传送门的指向改为某一位面的某一坐标。

#### `/portal set_portal_destination_to <entity>`

将传送门的指向改为某一实体的位置。

#### `/portal move_portal_destination <distance>`

将传送门的指向位置沿玩家看向的方向移动。

### 管理传送门{#Manage the Portal}

#### `/portal set_portal_nbt <nbt>`

修改传送门的NBT数据。[传送门NBT数据格式](https://github.com/qouteall/ImmersivePortalsMod/wiki/Portal-Attributes)

#### `/portal view_portal_data`

查看传送门的NBT数据。

#### `/portal delete_portal`

移除传送门。

#### `/portal move_portal <distance>`

将传送门沿玩家看向的方向移动。

#### `/portal set_portal_position <dimension> <x> <y> <z>`

更改传送门位置。

### Portal Clutter Management

[参见](https://github.com/qouteall/ImmersivePortalsMod/wiki/Portal-Customization#1-nether-portal--4-portal-entities)

#### `/portal complete_bi_way_portal`

创建新的传送门实体，使传送门变为双向的。重复的传送门会被移除。

#### `/portal complete_bi_faced_portal`

创建新的传送门实体，使传送门变为双面的。重复的传送门会被移除。

#### `/portal complete_bi_way_bi_faced_portal`

创建新的传送门实体，使传送门变为双向双面的。重复的传送门会被移除。

#### `/portal remove_connected_portals`

移除传送门实体，使传送门变为单向单面的。

#### `/portal eradicate_portal_clutter`

完全移除一个双向双面传送门（4个传送门实体）。等同于  `/portal remove_connected_portals` 和 `/portal delete_portal`

### 旋转变换{# Rotation}

#### `/portal set_portal_rotation <axisX> <axisY> <axisZ> <angleDegrees>`

设置传送门的旋转变换。

旋转变换由旋转轴向量与旋转角度组成。当旋转轴朝向你时，正的旋转角度相当于逆时针旋转。

#### `/portal set_portal_rotation_along <axis> <angleDegrees>`

与上一个类似，用 `x`, `y` or `z` 表示旋转轴。

#### `/portal rotate_portal_body <axisX> <axisY> <axisZ> <angleDegrees>`

旋转传送门本身。不改变传送门的旋转变换。

#### `/portal rotate_portal_body_along <axis> <angleDegrees>`

与上一个类似。

#### `/portal rotate_portal_rotation <axisX> <axisY> <axisZ> <angleDegrees>`

将传送门的旋转变换进行额外的旋转。

#### `/portal rotate_portal_rotation_along <axis> <angleDegrees>`

与上一个类似。

### 缩放{# Scale}

#### `/portal set_portal_scale <scale>`

设置传送门的缩放变换。

### 玩家区别性{#Player-specific Property}

#### `/portal set_portal_specific_accessor <player>`

将该传送门实体设置为只对一个玩家可见。

#### `/portal set_portal_specific_accessor`

将该传送门实体设置为不仅对某一玩家可见。

#### `/portal multidest <player> <dimension> <x> <y> <z> <isBiFaced> <isBiWay>`

This command modifies the portal clutter. It firstly removes the portals that are specific to the `player` and then adds new portals that specific to the `player` and point to the specified dimension and position. `isBiFaced` and `isBiWay` respectively controls whether the generated portal is bi-faced and bi-way.

#### `/portal multidest <player>`

Remove the player-specific portal from the portal clutter.

### Other

#### `/portal set_portal_custom_name <name>`

Set a portal entity's custom name. The custom name can be used for selecting the portal entity (for example @e[name="xxx"]).

#### `/portal make_portal_round`

Make the portal entity's shape to be an ellipse. If the portal's width equals height, the shape will be round.

## Direct Portal Creation Commands

Can be used by OPs and creative mode players.

#### `/portal make_portal <width> <height> <dimension> <toX> <toY> <toZ>`

Create a new portal coming off of the side of the block you're pointing at. The portal will face towards you.

#### `/portal make_portal <width> <height> <dimension> shift <distance>`

Create a portal whiches destination is `distance` blocks in front of the portal.

#### `/portal create_small_inward_wrapping <x1> <y1> <z1> <x2> <y2> <z2>`

Create a small inward wrapping zone. The generated portals are normal portals. (The global portal commands does not affect them.)

#### `/portal create_small_outward_wrapping <x1> <y1> <z1> <x2> <y2> <z2>`

Similar to the above but the wrapping zone is outward.

#### `/portal create_scaled_box_view <x1> <y1> <z1> <x2> <y2> <z2> <scale> <placeTargetEntity> <isBiWay> [teleportChangesScale]`

Create a scaled box wrapping zone. `<x1> <y1> <z1> <x2> <y2> <z2>` defines the inner box area. `<placeTargetEntity>` defines the outer box position. If `isBiWay` is true, it will generate the reverse portals for every portal. `teleportChangesScale` defines the generated portal's `teleportChangesScale` attribute.

The command sender dimension is the dimension of the view box. For example, if you want to create a box viewing the end island, use `/execute in minecraft:the_end run portal create_scaled_box_view -100 0 -100 100 128 100 20 @p true`
(`-100 0 -100 100 128 100` is a box with radius 100 on the end dimension, `20` is the scale, the outer box will be placed on `@p` 's position)


![](https://qouteall-1.oss-ap-northeast-1.aliyuncs.com/2020-08-26-21-18-54.png)

#### `/portal create_scaled_box_view_optimized <x1> <y1> <z1> <x2> <y2> <z2> <scale> <placeTargetEntity>`

Similar to the above but the created scale box has better rendering performance.

The outer portals will have "fuse view" enabled and "rendering mergable" enabled.
The inner portals will have "rendering mergable" enabled.
The portals will have "teleport changes scale" disabled.

This command requires that the scale box area is either aligned to chunk border (Press F3+G to see the chunk border) or does not have anything around that area (for example, a skyland). Because the merged portal rendering does not handle the front clipping well, if this requirement is not meet, the things outside the box may appear in view.

#### `/portal cb_make_portal <width> <height> <fromEntity> <toEntity>`

Create a portal entity that goes from `fromEntity` to `toEntity`. The portal's orientation is determined by `fromEntity` 's orientation.

## Miscellaneous Commands

Can be used by creative mode players or permission 2 ones.

#### `/portal tpme <dimension> <x> <y> <z>`

Teleport you across dimensions without any loading screen. Can only be invoked by players.

#### `/portal tp <entity> <dimension> <x> <y> <z>`

Teleport entities across dimensions.

#### `/portal goback`

Sometimes you went into a one-way portal and want to come back, but you forgot the coordinate where you come in. Use this command to come back.

## Debug Commands

Can be used by creative mode players or permission 2 ones.

#### `/portal debug gui_portal <dimension> <x> <y> <z>`

Load the chunks near the specific position and display a GUI portal for the player.
Used for testing GUI portal functionality.

For example, `/portal debug gui_portal minecraft:the_end 0 80 0`

![](https://qouteall-1.oss-ap-northeast-1.aliyuncs.com/2021-02-05-15-15-05.png)

Press ESC to quit.


####  `/portal debug isometric_enable <viewHeight>`

Enable the experimental isometric view for the player. `viewHeight` is the corresponding length of the screen height.

For example, `/portal debug isometric_enable 100`

![](https://qouteall-1.oss-ap-northeast-1.aliyuncs.com/2021-02-05-15-25-05.png)


Isometric view is implemented by replacing the projection matrix with the orthogonal projection matrix. Isometric view equivalents the camera being in an infinitely far place.

#### `/portal debug isometric_enable`

Quit the isometric view for the player.

#### `/portal debug align`

Align the player position by 0.5, set the yaw to be 45 degrees and set the pitch to be 30 degrees. Can be used for taking isometric screenshots.

#### `/portal debug create_command_stick <command>` 

Creates a command stick . For example `/portal debug create_command_stick "/say hi"`

This command requires level 2 permission.

## Deprecated Commands

These commands are deprecated. They will be removed in 1.17.

`/portal cb_set_portal_destination <portal> <dimension> <x> <y> <z>` `/portal cb_complete_bi_way_portal <portal>` `/portal cb_complete_bi_faced_portal <portal>` `/portal cb_complete_bi_way_bi_faced_portal <portal>` `/portal cb_remove_connected_portals <portal>` `/portal cb_set_portal_specific_accessor <portal> [player]` 

