**The API is still being worked on.**

This mod will have a big name/package rearrangement in the 1.17 update.

### Create a Portal

Example:

```
Portal portal = Portal.entityType.create(serverWorld);
portal.setOriginPos(new Vec3d(0, 70, 0));
portal.setDestinationDimension(World.NETHER);
portal.setDestination(new Vec3d(100, 70, 100));
portal.setOrientationAndSize(
    new Vec3d(1, 0, 0),//axisW
    new Vec3d(0, 1, 0),//axisH
    4,//width
    4//height
);
portal.world.spawnEntity(portal);
```

[Portal Attributes](https://github.com/qouteall/ImmersivePortalsMod/wiki/Portal-Attributes)

### Chunk Loading API

Vanilla has the force-load functionality but it only loads the chunk and does not synchronize the chunk to player client. This mod supports loading chunks and synchronize the chunk (blocks, entities, etc.) to the specific player.

Example:

```
PortalAPI.addChunkLoaderForPlayer(
    serverPlayerEntity,
    new ChunkLoader(
        new DimensionalChunkPos(
            World.OVERWORLD,
            100,//chunk x
            100//chunk z
        ),
        3//radius(chunks)
    )
);
```

Remove the chunk loader when you want to unload.

### Networking Utility (Remote Procedure Call)

Fabric provides the networking API. But adding a new type of packet requires  (1) Write packet serialization/deserialization code (2) Write the packet handling code,which requires sending the task to the client/server thread to execute it (3) Give it an identifier and register it. This networking utility makes it easier.


Example: if you want the server to send a packet to ask the client to invoke this method (on the render thread):

```
public class AAARemoteCallableBBB{
    public static void clientMethod(int arg1, double arg2) {...}
}
```

Do this

```
McRemoteProcedureCall.tellClientToInvoke(
    player,
    "path.to.the_class.AAARemoteCallableBBB.clientMethod",
    3, 4.5
);
```

If you want the client to send a packet to ask the server to invoke this method (on the server thread):

```
public class AAARemoteCallableBBB{
    public static void serverMethod(ServerPlayerEntity player, Block arg1) {...}
}
```

Do this

```
McRemoteProcedureCall.tellServerToInvoke(
    "path.to.the_class.AAARemoteCallableBBB.serverMethod",
    Blocks.STONE
);
```

For security concerns, the class path must contain "RemoteCallable". For example, the class name can be "XXRemoteCallableYYY" or "RemoteCallables".

The supported argument types are

* The types that Gson can directly serialize/deserialize,
     including `int`,`double`,`boolean`,`long`,`String`,`int[]`,`Map<String,String>`,Enums
* `Identifier`, `RegistryKey<World>`, `RegistryKey<Biome>`, `BlockPos`, `Vec3d`, `UUID`, `Block`, `Item`, `BlockState`, `ItemStack`, `CompoundTag`, `Text`

Using unsupported argument types will cause serialization/deserialization issues.

### GUI Portal

Use ` GuiPortalRendering.submitNextFrameRendering(worldRenderInfo, frameBuffer)` to ask it to render the world into the framebuffer in the next frame. The rendered dimension, position, camera transformation can be specified in the `WorldRenderInfo`

[Example](https://github.com/qouteall/ImmersivePortalsMod/blob/1.16/imm_ptl_core/src/main/java/com/qouteall/immersive_portals/api/example/ExampleGuiPortalRendering.java)

### Mod Structure

This mod (Fabric version)'s mod id is `immersive_portals`. It has 3 mods jar-in-jar.

* Immersive Portals Core (modid:`imm_ptl_core`)
* Cloth Config
* Mod Menu
  (Cloth Config and Mod Menu are used for providing the config GUI)

The Immersive Portals Core contains [the core portal functionality](https://github.com/qouteall/ImmersivePortalsMod/wiki/Implementation-Details):

* Recursive portal rendering (Rendering context management, transformation management, OpenGL state and framebuffer management)
* Client multi-world loading
* Remote chunk loading
* Remote chunk/entity networking synchronization
* Dimension transition without loading screen and multidimensional player position mutual synchronization
* Global portal management
* Cross portal block interaction
* Datapack-based custom portal generation (and general breakable portal)
* Integration with OptiFine, Sodium (my fork), Pehkui, (Requiem)

The Core registers portal entity types and portal placeholder block.
The Core (hopefully) does not change existing vanilla behavior.

The mod Immersive Portals has:

* Enhanced nether portals
* Enhanced end portal
* Alternate dimensions
* Dimension stack
* Command stick

### Configure Dependency

Add this into `repositories`

```
	maven { url 'https://jitpack.io' }
```

Add this into `dependencies`

```
modImplementation ('com.github.qouteall.ImmersivePortalsMod:imm_ptl_core:1.16-SNAPSHOT')
include 'com.github.qouteall.ImmersivePortalsMod:imm_ptl_core:1.16-SNAPSHOT'
```

See https://jitpack.io/#qouteall/ImmersivePortalsMod
(You can change `1.16-SNAPSHOT` to a release tag.)