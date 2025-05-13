---
layout: wiki
title: Armor and Weapon Types
base: items
---

There are 3 types of armor, each with varying levels of physical damage reduction and other stats
that benefit certain builds and playstyles.

## Armor

- [Light Armor](/wiki/light-armor)
- [Medium Armor](/wiki/medium-armor)
- [Heavy Armor](/wiki/heavy-armor)

There are 10 Armor Slots to place gear in, each providing that armor's stats to your character.

## Armor Slots

```
enum ARMOR_SLOTS {
	HEAD,
	SHOULDERS,
	GLOVES,
	CHEST,
	LEGS,
	BOOTS,
	TRINKET,
	LEFT_RING,
	RIGHT_RING,
	NECKLACE,
}
```

## Weapons

There are many flavors of weapon in the game, but mostly boil down to a few categories. One Handed
weapons can be dual wielded and Two Handed weapons require both hands.

### One Handed Weapons:
- swords, daggers, axes, maces, polearms, shields
 
### Two Handed Weapons:
- greatswords, greataxes, warhammer
 
### Ranged Weapons:
- bows

## Weapon Slots

There are 5 Weapon Slots to place gear in.

```
enum WEAPON_SLOTS{
	RIGHT_HAND,
	LEFT_HAND,
	BOW,
	ARROW,
	QUIVER,
}
```
