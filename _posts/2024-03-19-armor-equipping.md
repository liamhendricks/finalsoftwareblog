---
title: Devlog 1 - How Summoning does Armor Equipping
published: true
tag: summoning
---

{% include bilboard_image.html image-path="/assets/armor-equipping1.png" %}

# Armor Equpping in 3D

I'd like to share the techniques and strategies for how Summoning implemented armor equipping on our 3D characters. I thought this
would be an interesting topic because it is so central to the idea of RPGs, and also there is not a lot of good information about
how to make this work. Most tutorials are quite engine specific, required paid tools, or were overkill for my use case. So my hope
is that this gives devs some good information about how I was able to accomplish this in my game.

## Overall strategy

{% include bilboard_image.html image-path="/assets/armor-equipping2.png" %}
{% include bilboard_image.html image-path="/assets/armor-equipping4.png" %}

The idea is to create base character models that are fully rigged and vertex mapped. We can subdivide the model into multiple meshes
that will represent the different armor slots (head, shoulders, chest, gloves, legs and boots). We can copy this base character
model's blender file and create the armor set directly from that. We can texture the base mesh with armor textures, and add new
geometry. Doing it this way ensures that we will have the same vertex mapping and bone names in our armor sets. At runtime, we will
swap out the Mesh resource on the submesh for the corresponding one on the armor mesh. Everything should automagically match!

## Creating the models

{% include bilboard_image.html image-path="/assets/armor-equipping5.png" %}

As I said, our models will be subdivided into armor slots that we can target in-game. You can see the model is rigged and contains
vertex mappings for each bone. As long as our armor set models have the same armature (which I ensure by just starting each armor
set by copying the base character), and we take care to vertex map any new geometry, swapping these meshes at runtime will work with
zero issues.

{% include bilboard_image.html image-path="/assets/armor-equipping6.png" %}

I wanted all of my armor sets to be interchangeable. Meaning a character could be wearing the gloves from one set, the chest
from another set, the boots from another different set and so on. I realized that in order to make this work properly and keep
the models from interacting oddly (pants showing through a robe, etc etc) I would have to create and follow a few standards. I
created these rules arbitrarily, and your game may want to do it differently.

- Pants will always fit underneath shirts at the waist
- Boots will always fit underneath pants at the cuff
- Robes must go all the way to the boots
- If the leg armor is "shorts", it must contain the base character calves
- If chest armor is long sleeved, I must create a second chest piece that is short sleeved. This allows room for big gloves with
long sleeves

Also, there are a few things I had to solve with some scripting in-game and allowed me greater flexibility in creating armor sets.

- If the chest piece is a robe, hide the leg model. This ensures no legs poking through
- If the armor set contains skin texture, override that skin texture based on the character's race
- If the character has long hair, some helmet types may require that we hide the hair model
- If the gloves are large gloves, always use the short sleeve version of a particular chest model

I won't show do a demo of that functionality because it would require writing a full featured item system and that is a bit out of
scope. So hopefully you just get the idea that making this work in your game may require some scripting.

## Putting it together in the Godot Engine

{% include bilboard_image.html image-path="/assets/armor-equipping8.png" %}

I created a demo Godot project to show the implementation. Here we can see the female character after importing it into the engine.
I just made a new scene and added the female_character.glb to it. I used the "editable children" option to expand the created nodes
from the glb. I manually added the "Shoulders" `MeshInstance3D` node since the base character doesn't have one, but the armor sets
could have shoulder pieces.

{% include bilboard_image.html image-path="/assets/armor-equipping7.png" %}

Here is the corresponding armor scene.

{% include bilboard_image.html image-path="/assets/armor-equipping.gif" %}

As I explained, the idea is that we will simply swap out the Mesh resource on the base character, for the one on the armor set. Now,
in my real project, I have created a huge item system backed by a sql database and multiple components to manage the large number of
armor sets I have created (maybe a topic for another devlog ^^), but for the purposes of this little demo, I just created a simple
script to demonstrate. As you can see, the mesh continues to animate and everything looks great!

Basically this is all that is happening for each armor slot:

```
var b : MeshInstance3D = character.get_node("female_character/Armature/Skeleton3D/Boots")
var a : MeshInstance3D = armor.get_node("female_medium_armor/Armature/Skeleton3D/Boots")
b.mesh = a.mesh
```

Hopefully someone found this informative!
