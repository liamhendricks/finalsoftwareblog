---
title: Devlog 2 - Indoor / outdoor living
published: true
tag: summoning
---

{% include bilboard_image.html image-path="/assets/terrain6.png" %}

# Buildings, Terrain and Navigation -

Hello everyone! Today I wanted to write a bit about my proof of concept for open world navigation using Godot 4. Navigation is one
of the most complex systems in any open world game, and my decision to include buildings
in the open world did not make that any less complex. I realized as I was experimenting that there were concrete reasons why the
Bethesda games use instanced indoor scenes... It makes it much easier to do two things in particular: lighting and navigation. But
I want something different. Loading into and out of interiors is immersion breaking for me, and puts a limit on some
gameplay experiences. Assuming we can solve lighting and navigation, there's no reason why we can't do building interiors with no
loading screens.

Lighting in my case is no big deal, because I am personally happy with the way Godot's global illumination system interacts with
both outdoor and indoor locations. Navigation on the other hand was always going to be a challenge. Each building would need it's
own navigation mesh, but how would that interact with the global terrain navigation? I am using the fantastic
[Terrain3D Addon](https://github.com/TokisanGames/Terrain3D) for the open world, which allows you to paint navigation regions and
bake them. This works great and allows for multiple navigation regions. There was still the question of the best approach for doing
navigation in buildings.

## My strategy

{% include bilboard_image.html image-path="/assets/terrain0.png" %}

The idea is to create a navigation mesh for each building, and then use the automatic edge connections to bridge the gap between the
building and the terrain. This will allow me to create and maintain each building's nav mesh in it's own scene and then just worry
about placing the edges correctly. I essentially create little navigation 'holes' in the terrain and then place the building inside.

{% include bilboard_image.html image-path="/assets/terrain1.png" %}
{% include bilboard_image.html image-path="/assets/terrain2.png" %}

Terrain3D also supports multiple nav meshes on the terrain using the `filter_baking_aabb` setting. This allows for creating discrete
navigation regions all across the world while still allowing pathfinding between them. This enables an unlimited open world size
without pathfinding queries grinding your fps to a halt.

{% include bilboard_image.html image-path="/assets/terrain3.png" %}

Additionally, I use some settings that allow me to auto detect obstacles in the terrain and build nav around them, without having to
do the aforementioned 'holes' strategy for every little rock and tree that should not be navigable. I just have to place them as a
child of a node that is assigned to the 'town_obstacles' group, and it will automatically build nav around them.

{% include bilboard_image.html image-path="/assets/terrain4.png" %}
{% include bilboard_image.html image-path="/assets/terrain5.png" %}

Here's a lil gif showing some NPC pathfinding. He can even open the door for himself, isn't that nice?
{% include bilboard_image.html image-path="/assets/nav2.gif" %}

Just a short one here, but hope it was useful!
