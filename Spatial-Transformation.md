A portal stitches the existent space with a transformed space. It can have translation transformation, rotating transformation, scale transformation, and mirror transformation. Normal nether portals only have translation transformation. Here introduce the other transformations.

This mod's teleportation is eye-based. It means that the teleportation applies the transformation to the player's eye position. This makes the teleportation visually seamless. However, this doesn't guarantee that the player will be in empty space after teleporting.

## Rotation Transformation

![](https://qouteall.fun/imm_ptl_wiki_copy/assets/2020-08-06-12-18-32.png)

### Create a Portal with Rotation Transformation

#### In Survival Mode

- Enable `adaptive` mode [nether portal](https://github.com/qouteall/ImmersivePortalsMod/wiki/Portals#nether-portals). It allows linking the frames with different orientations.

- Using [datapack custom portal generation](https://github.com/qouteall/ImmersivePortalsMod/wiki/Datapack-Based-Custom-Portal-Generation). The form `imm_ptl:flipping_floor_square`, and `imm_ptl:try_hard_to_match` can generate portals with rotation transformation.

#### In Creative Mode

- Using [portal helper](https://github.com/qouteall/ImmersivePortalsMod/wiki/Portal-Customization#portal-helper-block) to create portals.

- Using [commands](https://github.com/qouteall/ImmersivePortalsMod/wiki/Portal-Customization). Command `/portal set_portal_rotation <axisX> <axisY> <axisZ> <angleDegrees>` can set a portal's rotation transformation. The rotating axis is a vector (axisX, axisY, axisZ).

### Teleportation

After crossing a portal with rotation transformation, the player's camera may be tilted. Then the camera rotation will smoothly turn into a valid state.

## Scale Transformation

![](https://qouteall.fun/imm_ptl_wiki_copy/assets/2020-08-06-12-34-27.png)

### Create a Portal with Scale Transformation

#### In Survival Mode

- Enable `adaptive` mode [nether portal](https://github.com/qouteall/ImmersivePortalsMod/wiki/Portals#nether-portals). It allows linking the frames with different scale.

- Enable `scaledView` mode of [end portal](https://github.com/qouteall/ImmersivePortalsMod/wiki/Portals#end-portals).

- Using [datapack custom portal generation](https://github.com/qouteall/ImmersivePortalsMod/wiki/Datapack-Based-Custom-Portal-Generation). The form `imm_ptl:scaling_square`, and `imm_ptl:try_hard_to_match` can generate portals with scale transformation.

#### In Creative Mode

- Using [portal helper](https://github.com/qouteall/ImmersivePortalsMod/wiki/Portal-Customization#portal-helper-block) to create portals.

- Using commands. Command `/portal set_portal_scale <scale>` sets a portal's scale transformation. Command `/portal create_scaled_box_view` [creates a scaled wrapping box](https://github.com/qouteall/ImmersivePortalsMod/wiki/Portal-Customization#create-a-scaled-wrapping-zone).

### Teleportation
The portal has a property `teleportationChangesScale`. If it's false, the entities that go through the portal will have the scale remain unchanged.
If it's true and [Pehkui mod](https://www.curseforge.com/minecraft/mc-mods/pehkui) is installed, teleportation will change the entity's scale.

If Pehkui mod is missing or you are using the Forge version, teleportation won't change the entity scale.

## Mirror Transformation

[Mirrors](https://github.com/qouteall/ImmersivePortalsMod/wiki/Portals#mirrors).

### Teleportation
Mirrors do not allow teleportation.
