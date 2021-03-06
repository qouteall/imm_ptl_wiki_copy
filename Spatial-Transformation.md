A portal is a window linking to a transformed space. The spacial transformation can be translation, rotation, scale and mirroring.

This mod's teleportation is eye-based. If an entity goes through a portal, it will calculate the entity's eye position transformed by the portal and then place the entity by the transformed eye position. 

## Rotation Transformation

![](https://i.ibb.co/LRGr8pK/2020-08-06-12-18-32.png)

[Commands related to rotation](https://github.com/qouteall/ImmersivePortalsMod/wiki/Commands-Reference#rotation)

### Teleportation

After crossing a portal with rotation transformation, the player's camera may be tilted. Then the camera rotation will smoothly turn into a valid state.

## Scale Transformation

![](https://i.ibb.co/T0xLjnP/2020-08-06-12-34-27.png)

[Commands related to scaling](https://github.com/qouteall/ImmersivePortalsMod/wiki/Commands-Reference#scale)

### Teleportation
The portal has a property `teleportationChangesScale`. If it's false, the entities that go through the portal will have the scale remain unchanged.
If it's true and [Pehkui mod](https://www.curseforge.com/minecraft/mc-mods/pehkui) is installed, teleportation will change the entity's scale.

If Pehkui mod is missing or you are using the Forge version, teleportation won't change the entity scale.

## Mirror Transformation

[Mirrors](https://github.com/qouteall/ImmersivePortalsMod/wiki/Portals#mirrors).

### Teleportation
Mirrors do not allow teleportation.