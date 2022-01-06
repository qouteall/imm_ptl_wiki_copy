A portal is a window linking to a transformed space. The spacial transformation can be translation, rotation, scale and mirroring.

This mod's teleportation is eye-based. If an entity goes through a portal, it will calculate the entity's eye position transformed by the portal and then place the entity by the transformed eye position. 

## Rotation Transformation

![image.png](https://i.loli.net/2021/11/20/2CHKJufPT6ILOxa.png)

[Commands related to rotation](https://github.com/qouteall/ImmersivePortalsMod/wiki/Commands-Reference#rotation)

### Teleportation

After crossing a portal with rotation transformation, the player's camera may be tilted. Then the camera rotation will smoothly turn into a valid state.

If the portal's property `teleportChangesGravity` is true, and [Gravity Changer mod](https://modrinth.com/mod/gravitychanger) is present, then your gravity direction will be transformed when you go through the portal.

## Scale Transformation

![image.png](https://i.loli.net/2021/11/20/6Y9dimqOSn8NUxA.png)

[Commands related to scaling](https://github.com/qouteall/ImmersivePortalsMod/wiki/Commands-Reference#scale)

### Teleportation
The portal has a property `teleportationChangesScale`. If it's false, the entities that go through the portal will have the scale remain unchanged.

If it's true and [Pehkui mod](https://www.curseforge.com/minecraft/mc-mods/pehkui) is installed, teleportation will change the entity's scale.

If Pehkui mod is missing or you are using the Forge version, teleportation won't change the entity scale.

## Mirror Transformation

[Mirrors](https://github.com/qouteall/ImmersivePortalsMod/wiki/Portals#mirrors).

### Teleportation
Mirrors do not allow teleportation.