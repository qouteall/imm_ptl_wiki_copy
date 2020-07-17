(this feature hasn't been released. working in progress)

This feature is 1.16 only.

Configure custom portal generations using json files in a datapack.

[What are datapacks and how to install them](https://minecraft.gamepedia.com/Data_Pack)

## Example

[Download the example datapack](https://github.com/qouteall/ImmersivePortalsMod/raw/1.16/example_custom_portal_gen.zip)

#### The glowstone portal that's activated using a water bucket from overworld to alternate2 dimension.
Similar to the aether portal.
```
{
  "schema_version": "imm_ptl:v1",
  "from": [
    "minecraft:overworld"
  ],
  "to": "immersive_portals:alternate2",
  "form": {
    "type": "imm_ptl:classical",
    "from_frame_block": "minecraft:glowstone",
    "area_block": "minecraft:air",
    "to_frame_block": "minecraft:glowstone",
    "generate_frame_if_not_found": true
  },
  "trigger": {
    "type": "imm_ptl:use_item",
    "item": "minecraft:water_bucket"
  }
}
```
#### A floor flipping portal to alternate1. Activated by throwing diamond to a 2x2 water pool surrounded by dirt with flowers on top.
Similar to the twilight forest portal. It will summon a lightning bolt after creating the portal.
```
{
  "schema_version": "imm_ptl:v1",
  "from": [
    "minecraft:overworld"
  ],
  "to": "immersive_portals:alternate1",
  "form": {
    "type": "imm_ptl:flipping_floor_square",
    "length": 2,
    "frame_block": "minecraft:bamboo_plantable_on",
    "area_block": "minecraft:water",
    "up_frame_block": "minecraft:small_flowers",
    "bottom_block": "minecraft:bamboo_plantable_on"
  },
  "trigger": {
    "type": "imm_ptl:throw_item",
    "item": "minecraft:diamond"
  },
  "post_invoke_commands": [
    "/summon minecraft:lightning_bolt ~ ~ ~"
  ]
}
```
#### From overworld to alternate4. The overworld side frame is lapis block, but the other side's frame is redstone block.
And for this portal one block in overworld corresponds to 8 blocks in alternate4.
```
{
  "schema_version": "imm_ptl:v1",
  "from": [
    "minecraft:overworld"
  ],
  "to": "immersive_portals:alternate4",
  "space_ratio_from": 1,
  "space_ratio_to": 8,
  "form": {
    "type": "imm_ptl:classical",
    "from_frame_block": "minecraft:lapis_block",
    "area_block": "minecraft:air",
    "to_frame_block": "minecraft:redstone_block",
    "generate_frame_if_not_found": true
  },
  "trigger": {
    "type": "imm_ptl:use_item",
    "item": "minecraft:flint_and_steel"
  }
}
```
#### Similar to portal helper but using diamond block as frame and breakable.
```
{
  "schema_version": "imm_ptl:v1",
  "from": [
    "minecraft:overworld",
    "minecraft:the_nether",
    "minecraft:the_end"
  ],
  "to": "imm_ptl:the_same_dimension",
  "reversible": false,
  "form": {
    "type": "imm_ptl:classical",
    "from_frame_block": "minecraft:diamond_block",
    "area_block": "minecraft:air",
    "to_frame_block": "minecraft:diamond_block",
    "generate_frame_if_not_found": false
  },
  "trigger": {
    "type": "imm_ptl:use_item",
    "item": "minecraft:flint_and_steel"
  }
}
```
#### From overworld to alternate5. The frame can be in any type of wood planks. Activated using a compass.
```
{
  "schema_version": "imm_ptl:v1",
  "from": [
    "minecraft:overworld"
  ],
  "to": "immersive_portals:alternate5",
  "form": {
    "type": "imm_ptl:heterogeneous",
    "frame_block": "minecraft:planks",
    "area_block": "minecraft:air",
    "generate_frame_if_not_found": true
  },
  "trigger": {
    "type": "imm_ptl:use_item",
    "item": "minecraft:compass"
  }
}
```
#### A new type of nether portal. Throw an netherite into a 3x3 lava pool surrounded by soul soil blocks. Can only be created in overworld
```
{
  "schema_version": "imm_ptl:v1",
  "from": [
    "minecraft:overworld"
  ],
  "to": "minecraft:the_nether",
  "reversible": false,
  "form": {
    "type": "imm_ptl:flipping_floor_square",
    "length": 3,
    "frame_block": "minecraft:soul_soil",
    "area_block": "minecraft:lava"
  },
  "trigger": {
    "type": "imm_ptl:throw_item",
    "item": "minecraft:netherite_ingot"
  }
}
```

## Details Explained

The datapack-based custom portal generation system allows configuring special portal generation mechanics. The portal generation can be triggered by using an item or throwing an item into some position. It can be configured to only apply to one dimension, and specify the portal's destination dimension. The space ration can be configured to determine where the destination should be. A list of commands can be specified to be invoked after portal creation. There are different portal forms each with different kinds of portal and different destination selection mechanics.

All the generated portals will be `immersive_portals:general_breakable_portal`. They will generate with placeholder blocks filling the area. And they will break if the frame is broken. (Placeholder blocks have illumination)

The custom portal gen json should be located in `data/imm_ptl/custom_portal_generation/<namespace>`. The json file name does not matter.

### The Codec of Custom Portal Generation
* `schema_version` String. Must be `imm_ptl:v1`.
* `from` List of dimension ids. The dimensions that this generation can perform in.
* `to` Dimension id. The destination dimension's id. A special case: if it's `imm_ptl:the_same_dimension`, the destination dimension will be the same as the from dimension.
* `space_ratio_from` Integer (1 as default). This side dimension's space ratio.
* `space_ratio_to` Integer (1 as default). The other side dimension's space ratio. Together with the above defines the space mapping. For example, 8 blocks' length in overworld corresponds to 1 block's length in the nether. The overworld's space ratio is 8 and the nether's space ration is 1.
* `reversible` Boolean (true as default). If true, the reverse version of this generation will also be added. If you configured a portal from overworld to nether with reversible false, then the portal can only be activated in the overworld. If it's true then the portal can also be activated in the nether.
* `form` Custom portal generation form. Described below.
* `trigger` Custom portal generation trigger. Described below.

### The Codec of Custom Portal Generation Form
 
 
