### Creating a Portal Entity

Check [this](https://github.com/qouteall/ImmersivePortalsMod/wiki/Portal-Customization) to have an idea about how this mod's portal is stored and organized.

You can create a [Portal](https://github.com/qouteall/ImmersivePortalsMod/blob/1.15/src/main/java/com/qouteall/immersive_portals/portal/Portal.java)
entity, initialize its data and then add it into the world.
`axisW` and `axisH` should be perpendicular. These two vectors defines the facing of the portal.

If `specialShape` is null then the portal is rectangular. [GeometryPortalShape](https://github.com/qouteall/ImmersivePortalsMod/blob/1.15/src/main/java/com/qouteall/immersive_portals/portal/GeometryPortalShape.java) is a set of 2D triangles. This 2D coordinate's x axis is `axisW`, y axis is `axisH`.

If you created one portal entity, you can add a new portal to complete the bi-way portal or bi-faced portal.[PortalManipulation](https://github.com/qouteall/ImmersivePortalsMod/blob/1.15/src/main/java/com/qouteall/immersive_portals/portal/PortalManipulation.java)

You can also create breakable portals using [BlockPortalShape](https://github.com/qouteall/ImmersivePortalsMod/blob/1.15/src/main/java/com/qouteall/immersive_portals/portal/nether_portal/BlockPortalShape.java) by `NetherPortalGeneration#generateBreakablePortalEntities`. It's needed to create a new subclass of BreakablePortalEntity. Check [NetherPortalEntity](https://github.com/qouteall/ImmersivePortalsMod/blob/1.15/src/main/java/com/qouteall/immersive_portals/portal/nether_portal/NetherPortalEntity.java). Breakable portal has placeholder blocks to fill the portal area. If the placeholder block updates, nearby breakable portals will be notified to check portal integrity.

### How to depend on Immersive Portals

Use [CurseMaven](https://github.com/Wyn-Price/CurseMaven) to automatically get the mod from [CurseForge](https://www.curseforge.com/minecraft/mc-mods/immersive-portals-mod).

1. In your `plugins` block at the top of build.gradle add this at the end:

   ```
   	id "com.wynprice.cursemaven" version "2.1.1"
   ```

   This will add CurseMaven as a plugin and allow you to use curse.maven in your dependencies.

2. Go to the [files tab on CurseForge](https://www.curseforge.com/minecraft/mc-mods/immersive-portals-mod/files) and pick the version you want. Click the purple download button. Look in your address bar and you will see something like:

   `https://www.curseforge.com/minecraft/mc-mods/immersive-portals-mod/files/2936532`

   The long number at the end is the version you want. In this case it's `2936532`. You can close the tab now because you don't need to download the file to your computer, CurseMaven will do it for you. But remember to copy the number and put it somewhere.

3. In your `dependencies` block in build.gradle put:

   ```
   	modImplementation "curse.maven:immersive-portals-mod:2936532"
   ```

   `curse.maven` tells it to use the CurseMaven plugin, `immersive-portals-mod` is the mod id on Curse, and `2936532` is the file id.

4. Rerun gradle sync from your IDE and you should be able to access `Portal` class from `com.qouteall.immersive_portals.portal`. Or any other class in this mod.

### Using Gradle 6

If you, for whatever reason, decided to upgrade your Gradle version from 5 to 6, CurseMaven may not work. In that case you can use Jitpack. Add this to your repositories block:

```
	maven { url 'https://jitpack.io' }
```

Then you can depend on the mod like so:

```
	modImplementation 'com.github.qouteall:ImmersivePortalsMod:0.28-1.15-1'
```