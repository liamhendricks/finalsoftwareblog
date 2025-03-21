---
title: Devlog 2 - Indoor / outdoor living
published: true
tag: summoning
---

{% include bilboard_image.html image-path="/assets/indoor-outdoor1.png" %}

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

{% include bilboard_image.html image-path="/assets/indoor-outdoor2.png" %}

The idea is to create a navigation mesh for each building, and then use [NavigationLink3D](https://docs.godotengine.org/en/stable/tutorials/navigation/navigation_using_navigationlinks.html) to allow for Navigation between each
building and the terrain. This will allow me to create and maintain each building's nav mesh in it's own scene and then just worry
about the link in the open world. The main downside I have discovered is that ensuring the NavigationLink works is more of an art
than a science. Placing the endpoints of the link requires a fair amount of trial and error, and manual testing to make sure
Navigation Agents can cross the link. This could prove to be annoying as I build towns that require me to manually test many links,
so there could be room for improvement in that respect. Not a whole lot of information exists online about NavigationLink, so it's
entirely possible that I am missing something.

I encourage you to read through the documentation page for NavigationLink3D that I linked above. Essentially what it does is provide
a "bridge" between Navigation Regions.

{% include bilboard_image.html image-path="/assets/nav.gif" %}

Here is a gif of one of my NPCs walking into a building (and crossing Navigation Regions through the link). He even opens the door
for himself :)

Just a short one here, but hope it was useful!
