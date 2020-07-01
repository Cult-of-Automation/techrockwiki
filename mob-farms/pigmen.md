---
title: Forced portal spawning
description: 
published: true
date: 2020-02-25T17:49:35.142Z
tags: 
---

# Portal Ticking

**Portal Ticking** is a mechanic only available in **Minecraft: Bedrock Edition** which refers to artificially accelerating spawning of zombie pigmen through nether portals by implementing a mechanism that repeatedly lights and unlights the nether portal. This can be used to create high output zombie pigman farms, which produce large amounts of experience and gold at a high obsidian efficiency.

## Base Mechanics

In **Bedrock Edition**, nether portal blocks that are selected by a randomTick have a 11/2000 chance (Note: this chance only applies to **Hard** difficulty. It will be lower on other difficulties.) of spawning a zombie pigman. This **only occurs in the overworld dimension**.
Zombie pigman spawning through this mechanic will not be affected by any mob caps, but will count towards the **surface hostile mob cap**.
Zombie pigmen that spawn through this mechanic will always appear to the south or east side of a nether portal, depending on its orientation. These zombie pigmen will always spawn at the lowest block of the portal. If blocks are present, they will spawn inside of them and suffocate.

## Portal Ticking

In normal conditions, a nether portal will only spawn pigmen if naturally selected by a randomTick defined by the ``randomtickspeed`` gamerule. 

However, when a portal is lit, all of the existing nether portal tiles will have a 11/2000 chance to spawn a zombie pigman, which vastly accelerates the pace at which zombie pigmen can spawn through a portal.

With this mechanic in mind, advanced zombie pigmen farms can be created.

## Creating A Zombie Pigman Farm

Zombie pigman farms that make use of this mechanic are subject to many issues if not properly executed.

### Portal Breaking Systems

Portals have to be broken by dispensing a water or lava bucket inside of the obsidian frame of a portal. Despite water flowing faster, lava will be affected by randomTicks and will spiral out of control after a given amount of time, making water preferrable. 
Systems that make use of this to break portals have to take into account that a single dispenser can only get pulsed and thus dispense and pick up a liquid source every 4 game ticks. Using a single dispenser will cause issues as both water and lava may flow out after a while of usage.
Circuits that make use of two dispensers to dispense a source and picks it up 2 game ticks later are proven to be more reliable. However, due to the **Bedrock Edition Update Order**, they cannot merely be pulsed repeatedly. A special although simple circuit that alternates which dispenser gets pulsed first resolves those issues. Unloading such a circuit while running will potentially mess up the resting state of the liquid and remove the buckets from their proper dispenser.

### Portal Lighting

Portals can be relit by setting wooden blocks on fire. This requires the ``dofiretick`` gamerule to be set to ``true``. Should this not be the case, a system utilizing e.g. Flint & Steel has to be used to relight the portals. Iron ingot consuption will be about half of the gold ingot gain (*Verify*.)

Using wooden blocks to relight portals has two different variations.

The first involves wooden blocks that spread fire, but don't burn themselves. Those blocks are trapdoors, crafting tables and wooden buttons (*Verify*). Other wooden blocks burn themselves.
Spreading fire occurs through adjacent lava blocks. Lava blocks will spread fire naturally when they flow, or when selected by a randomTick. This method has been observed to possess a form of directionality. In order to bypass this, one has to block off all sides adjacent to the wooden block except for the one inside of the portal frame to guarantee lack of directionality.
Fire spread through lava can also be accelerated by rapidly updating blocks adjacent to the lava blocks. An easy way of doing so is an observer clock (2 observers facing each other).
The lava will need one air block or wooden blocks above it in order to spread fire.

The second involves wooden blocks that burn themselves. All wooden blocks that are not listed above are included (*Verify*).
By setting the side of one of these blocks on fire which is inside of a nether portal frame, the portal can be relit. The sides of these blocks can be set on fire through regular fire, and no artificial lava flow is required. Fire will have to be on netherrack, to prevent decay.
However, this method has been proven to break over time. One wooden block will burn off over time, exposing adjacent sides of other wooden blocks, which will allow the fire to spread.

### Farming The Pigmen

The produced zombie pigmen will always appear **south or east** to the nether portal from which they originate. This leaves a variety of ways to farm the pigmen open.

The most commonly used method is a **trident killer**. Trident killers are circuits that push tridents which will result in them dealing damage to any mob in contact. When holding a sword enchanted with Looting 3, the zombie pigmen will be affected by the Looting enchantment. Zombie pigmen killed by trident killers drop experience. Zombie pigmen killed by trident killers **do not drop golden swords**.
In order to move the zombie pigmen from their spawning location to a trident killer, water streams, sand pushers or luring through player or snow golem aggroing can be used. Aggroing has a maximum radius of 20 blocks and will not chain, making it a unreliable method of moving zombie pigmen as fall damage has to be sacrificed, which prevents the pigmen from being killed fast enough.
(Note: With the removal of gravity block stacking since the 1.15.0.51 Beta, conventional sand pushers are not viable.)
Weakening the pigmen through fall damage is **vital** should the pigmen output be very high. Otherwise, the zombie pigmen spawning can outspeed the killing pace and potentially crash worlds.
Should trident killers ever get removed in the future, swords with autoclickers can be used as a viable alternative for AFK Looting and experience. In the same setup, swords without an autoclicker or Harming potions can also be used for manual killing.

Alternatively, the zombie pigmen can be killed by fall damage. The pigmen will spawn in air south or east to their portal and fall to their death.
Zombie pigmen will also spawn inside of blocks that are south or east to their portal and suffocate.
**Note that neither of these methods will provide Looting or experience.** Both can be used to weaken the zombie pigmen though.

Zombie pigmen are immune to **fire, lava and magma** damage.

## Additional Information
Chunks possess an update cap of 100 pendingTicks for every game tick. Should the amount of pendingTicks in one game tick exceed this cap, it will get delayed to the next game tick. Portal ticking causes pendingTick updates, which can potentially build up over time. This can delay spawning of pigmen, even after the portal ticking process is stopped. Buildup of pendingTick updates can also be harmful to your world.