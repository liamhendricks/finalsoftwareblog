---
layout: wiki
title: Building your Character
base: home
---
Each character must choose 3 primary skills. These will be the only skills available to the player
during his or her playthrough. Each primary skill has many abilities available to use, and finding
synergy between the three primary skills is crucial to creating a good build.

```
enum PRIMARY_SKILLS {
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
}
```

Characters may weild any weapon, regardless of skill choice, but the weapon skills will not be
trainable unless chosen as a primary skill. For example, any character mayweild a dagger weapon, but
only characters who have chosen [Daggers](/wiki/daggers) as a primary skill can use the
[Backstab](/wiki/backstab) ability.

There will be an opportunity during the middle of the playthrough (many hours in) where players may
complete a long quest chain to respec their skills and allocated attributes. It is not easy, and
you may only do it once per playthrough.
