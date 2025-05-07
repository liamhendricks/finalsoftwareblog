---
layout: wiki
title: Spell Schools and Damage Types
---

There are 26 Spell Schools in the game, matching up with each of the cooresponding primary or
secondary skills. A Spell School is really just a way to categorize a Spell by type.

## Spell Schools

```
enum SPELL_SCHOOLS {
	PHYSICAL,
	MAGICAL,
	ONE_HAND,
	DAGGERS,
	TWO_HAND,
	ARCHERY,
	FROST,
	FIRE,
	HOLY,
	NATURE,
	BLOOD,
	NECROMANCY,
	DISCIPLINE,
	ANIMAL_HANDLING,
	PERSONALITY,
	ATHLETICS,
	PROTECTION,
	HEAVY_ARMOR,
	MEDIUM_ARMOR,
	LIGHT_ARMOR,
	IDENTIFICATION,
	SURVIVAL,
	THIEVERY,
	STEALTH,
	MYSTICISM,
	MEDICINE,
}
```

## Damage Types

Each of the standard damage types applies a debuff. Melee and ranged only apply on crit.

### Fire:
- Applied by abilities in the Fire spell school.
- Causes [Burn](/wiki/burn)
 
### Frost:
- Applied by abilities in the Frost spell school.
- Causes [Frostbite](/wiki/frostbite)
 
### Nature:
- Applied by abilities in the Nature spell school.
- Causes [Rot](/wiki/rot)

### Holy:
- Applied by abilities in the Holy spell school.
- Causes [Judgement](/wiki/judgement)
 
### Blood:
- Applied by abilities in the Blood spell school.
- Causes [Drain](/wiki/drain)
 
### Melee (crit):
- Applied by melee weapon attacks, and abilities in the One Hand, Two Hand and Daggers spell 
schools.
- Causes [Bleed](/wiki/bleed)
 
### Ranged (crit):
- Applied by bow attacks, and abilities in the Archery spell school.
- Causes [Bleed](/wiki/bleed)

## Disabling Effects

These are combat effects that inflict a loss of control of a character in one way or another.

- [Stun](/wiki/stun)
- [Silence](/wiki/silence)
- [Immobilize](/wiki/immobilize)
