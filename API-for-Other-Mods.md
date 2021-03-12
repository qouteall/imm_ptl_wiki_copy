**The API is still being worked on.**

This mod will have a big name/package rearrangement in the 1.17 update.

The API is mainly designed for Fabric.

### Create a Portal

Example:

```
Portal portal = Portal.entityType.create(serverWorld);
portal.setOriginPos(new Vec3d(0, 70, 0));
portal.setDestinationDimension(World.NETHER);
portal.setDestination(new Vec3d(100, 70, 100));
portal.setOrientationAndSize(
    new Vec3d(1, 0, 0), // axisW
    new Vec3d(0, 1, 0), // axisH
    4, // width
    4 // height
);
portal.world.spawnEntity(portal);
```

The portal can face any rotation, be anywhere, point to any position in any dimension.

It's recommended to check [Portal Attributes](https://github.com/qouteall/ImmersivePortalsMod/wiki/Portal-Attributes) .

![](https://i.ibb.co/2djwR8C/axis.png)

`axisW` and `axisH` are unit vectors and should be perpendicular to each other. The portal orientation has nothing to do with pitch and yaw (because pitch and yaw cannot represent all rotations).

If the portal attribute gets changed on the server side after the portal has spawned, call `reloadAndSyncToClient` to sync the changes to client.

To create the reverse/flipped portal entity, use `PortalAPI.createReversePortal` `PortalAPI.createFlippedPortal` . [How bi-way portals and bi-faced portals are organized](https://github.com/qouteall/ImmersivePortalsMod/wiki/Portal-Customization#1-nether-portal--4-portal-entities)

#### About Rotations and Quaternions

You can set the portal's rotating transformation by `setRotationTransformation()` . The rotation transformation is represented using quaternion. There is a vanilla quaternion class `net.minecraft.util.math.Quaternion` and IP's quaternion class `DQuaternion`. The vanilla quaternion uses float and is mutable. `DQuaternion` uses double and is immutable.

A quaternion is a rotating transformation. For example you can create a rotation along Y axis for 45 degrees by `DQuaternion.rotateByDegrees(new Vec3d(0,1,0),45).toMcQuaternion()` . 

Normally you don't need to care about the four numbers in quaternion. You just need to know these: 

* A quaternion can be seen as a unit 4D vector, or a point on a 4D unit sphere surface. If the 4D vector is not unit-length, the rotation will not function normally. 
* Hamilton product combines two rotating transformations. The sequence matters.
* Conjugate means getting the inverse rotation.
* Having the 4 numbers negated does not change the corresponding rotation. 
* The quaternion can be interpolated on the 4D sphere surface.

IP does not use Euler angle for rotation because Euler angle requires handling many edge cases and is more complex.

### Chunk Loading API

Vanilla has the force-load functionality but it only loads the chunk and does not synchronize the chunk to player client. This mod supports loading chunks and synchronize the chunk (blocks, entities, etc.) to the specific player.

Example:

```
PortalAPI.addChunkLoaderForPlayer(
    serverPlayerEntity,
    new ChunkLoader(
        new DimensionalChunkPos(
            World.OVERWORLD,
            100, // chunk x
            100 // chunk z
        ),
        3 // radius in chunks
    )
);
```

Call `removeChunkLoaderForPlayer` when you want to unload.

### Access Multiple Client Worlds

This mod eliminates the limitation that only one dimension can be loaded on client at the same time. For example, if you want to get the nether world, use `ClientWorldLoader.getWorld(World.NETHER)` . The client world will be created when it's used at the first time.

If the client experiences conventional dimension change (with loading screen) then all worlds will be unloaded and recreated later.

### Dimension API

In 1.16 most mods use datapack functionality to add new dimensions. However, using the datapack has these drawbacks:

* It stores all dimension options into `level.dat`. Upon upgrading, DFU cannot recognize non-vanilla generator types and swallows the nether and the end. [See also](https://github.com/TelepathicGrunt/Bumblezone-Fabric/issues/20)
* It requires the generator's seed to be hardcoded.
* Upon entering a world, the game shows the warning screen (worlds using experimental settings are not supported).

IP's dimension API overcomes these obstacles. To use the IP dimension API, you need to keep the dimension type json and delete the dimension json. Then do this during initialization:

```
IPDimensionAPI.onServerWorldInit.connect((generatorOptions, registryManager) -> {
    SimpleRegistry<DimensionOptions> registry = generatorOptions.getDimensions();
    long seed = generatorOptions.getSeed();
    
    // get the dimension type
    DimensionType dimensionType = registryManager.get(Registry.DIMENSION_TYPE_KEY)
        .get(new Identifier("namespace:dimension_type_id"));
    Validate.notNull(dimensionType);
    
    // get the biome registry for initializing the biome source
    MutableRegistry<Biome> biomeRegistry = registryManager.get(Registry.BIOME_KEY);
    BiomeSource biomeSource = new CustomBiomeSource(seed, biomeRegistry);
    
    // directly register the dimension
    Identifier dimensionId = new Identifier("namespace:dimension_id");
    IPDimensionAPI.addDimension(
        seed, registry, dimensionId, () -> dimensionType,
        new CustomChunkGenerator(seed, biomeSource)
    );
    
    // mark it non-persistent so it won't be saved into level.dat
    IPDimensionAPI.markDimensionNonPersistent(dimensionId);
});
```

(The `Signal` is similar to the event.)

### Networking Utility (Remote Procedure Call)

Fabric provides the networking API. But adding a new type of packet requires  (1) Write packet serialization/deserialization code (2) Write the packet handling code, which requires sending the task to the client/server thread to execute it (3) Give it an identifier and register it. This networking utility makes it easier.


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

For security concerns, the invoked method's class path must contain "RemoteCallable". For example, the class name can be "XXRemoteCallableYYY" or "RemoteCallables".

The supported argument types are

* The types that Gson can directly serialize/deserialize,
     including `int`, `double`, `boolean`, `long`, `String`, `int[]`, `Map<String,String>`, Enums, Plain old java objects
* `Identifier`, `RegistryKey<World>`, `RegistryKey<Biome>`, `BlockPos`, `Vec3d`, `UUID`, `Block`, `Item`, `BlockState`, `ItemStack`, `CompoundTag`, `Text`

Using unsupported argument types will cause serialization/deserialization issues.

### GUI Portal

Use ` GuiPortalRendering.submitNextFrameRendering(worldRenderInfo, frameBuffer)` to ask it to render the world into the framebuffer in the next frame. The rendered dimension, position, camera transformation can be specified in the `WorldRenderInfo`

That framebuffer will automatically be resized to be the same size as the game window.

[Example](https://github.com/qouteall/ImmersivePortalsMod/blob/1.16/imm_ptl_core/src/main/java/com/qouteall/immersive_portals/api/example/ExampleGuiPortalRendering.java)



### Mod Structure

This mod (Fabric version)'s mod id is `immersive_portals`. It has 3 mods jar-in-jar.

* Immersive Portals Core (modid:`imm_ptl_core`)
* Cloth Config
* Mod Menu
  (Cloth Config and Mod Menu are used for providing the config GUI)

The Immersive Portals Core contains [the core portal functionality](https://github.com/qouteall/ImmersivePortalsMod/wiki/Implementation-Details):

* Recursive portal rendering (Rendering context management, transformation management, OpenGL state and framebuffer management) and GUI portal rendering
* Client multi-world loading
* Server-side remote chunk loading
* Remote chunk/entity networking synchronization
* Client dimension transition without loading screen
* Multidimensional player position mutual synchronization
* Global portal management
* Cross portal block interaction, cross portal sound
* Cross portal entity rendering
* Cross portal collision handling
* Datapack-based custom portal generation (and general breakable portal)
* Integration with OptiFine, Sodium (my fork), Pehkui
* Dimension API

The Core registers portal entity types and portal placeholder block.
The Core (hopefully) does not change existing vanilla behavior.

The mod Immersive Portals has:

* Enhanced nether portals
* Enhanced end portal
* Alternate dimensions
* Dimension stack
* Command stick
* Portal helper

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

