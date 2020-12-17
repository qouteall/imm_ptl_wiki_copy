(A full set of APIs for other mods to use haven't been fully implemented. It's being worked on.)

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
* Extended reach in creative mode

### Configure Dependency
#### If you want to use Immersive Portals Core and have it as a jar-in-jar

Add this into `repositories`
```
	maven { url 'https://jitpack.io' }
```
Add this into `dependencies`

```
	modImplementation  'com.github.qouteall.ImmersivePortalsMod:imm_ptl_core:1.16-SNAPSHOT'
        include 'com.github.qouteall.ImmersivePortalsMod:imm_ptl_core:1.16-SNAPSHOT'
```
See https://jitpack.io/#qouteall/ImmersivePortalsMod
(You can change `1.16-SNAPSHOT` to a release tag. If Jitpack doesn't work, try to fork this repo and use the forked repo)

#### If you want to have an optional dependency of Immersive Portals (some functionality only enables with IP installed)
```
	modCompileOnly 'com.github.qouteall.ImmersivePortalsMod:imm_ptl_core:1.16-SNAPSHOT'
```

### API Briefly Explained

There are two kinds of portals:
* Portal Entities in World
They exist as entities in the world. They cannot be very big.
* Global Portals
They are also portal entities but not added to the world. They can be very big.

A portal has these properties
* The world in which the entity is.
* The entity position. The center of the portal
* axisW and axisH vector. Defines the orientation of the portal. These two vectors have to be perpendicular.
* width, height. The area of the portal.
* dimensionTo. The destination dimension.
* destination. The destination position.
* rotation (optional). The rotation transformation.
* scaling. The scaling transformation.
* specialShape (optional). A list of triangles on the portal plane that defines the shape of the portal. If this is null then the portal is rectangular.
* specificPlayerId (optional). If not null, only the player with this id can see and access this portal.
* teleportable. Whether the portal can teleport entities.
* cullableXStart, cullableXEnd, cullableYStart, cullableYEnd. Used for advanced frustum culling. These 4 numbers define a rectangular area on the portal plane. The portal shape must cover this area. All the chunk sections fully behind this area's projection from the camera will be culled to increase portal rendering performance. If these 4 numbers aren't configured correctly, the chunks behind the portal may be incorrectly culled. If you create an irregular shaped portal, you can set them to 0 so that the culling issue won't happen to this portal.
* teleportChangesScale. If the portal has scale transformation, it defines whether the entity going through it should change the scale.
* extension.motionAffinity. If positive, the player colliding with it will be accelerated. Vice versa.
* extension.adjustPositionAfterTeleport. If true, when the player collides with the floor after teleporting through the portal, the player will be smoothly levitated to avoid falling into the floor.

To add a portal entity, create the portal entity object, change the properties, add it into the world. Note that if you change a property on the server side, it doesn't automatically sync to the client side.

Every portal entity is one-faced and one-way. There are some helper functions: `PortalManipulation.createReversePortal` `PortalManipulation.createFlippedPortal`.

The appropriate API of this mod is still being worked on. Most code is not documented. If you have any questions ask qouteall.