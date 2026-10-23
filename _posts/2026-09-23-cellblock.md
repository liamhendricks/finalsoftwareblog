---
title: Building Open world games with Cellblock
published: true
tag: summoning
---

{% include youtube_player.html id="c7-dZm9I0gY" %}

Apologies for the terrible video editing and microphone quality. I'm not experienced with
creating videos. Get Cellblock here: [Cellblock](https://github.com/liamhendricks/cellblock/releases)

# Cellblock v0.6.0

About 6 months ago I decided to open source the first version of my data driven scene management
addon called [Cellblock](https://github.com/liamhendricks/cellblock/). Since then, a ton of work
has been done to improve the usability of the tool, brighten the documentation, and provide
stability to a very powerful workflow. As of right now, I have pushed v0.6.0, and I feel like the
addon is in a great place for general purpose use. So here is a simple overview on the design 
of Cellblock. I hope you enjoy!

# Text Overview

Here is the text-based version for those of you that hate watching videos:

Hello everyone. It's been 6 months since I released the initial version of Cellblock, and now with
the release of v0.6.0, I finally have a video. Cellblock is a data driven scene management plugin
for the Godot engine, created to support open world game development in Godot. It handles the
loading and unloading of game content at runtime, and enables a data driven workflow in the Godot
editor that allows developers to build and scale large worlds. It supports saving and loading out
of the box, and works great alongside other addons such as Terrain3D, AssetPlacer, and 
HungryProton's Scatter.

Why is this addon necessary? And how does it help build open world games? Open world game devs are
faced with some unique problems that must be tackled. Game content should only be loaded in a
radius around the player. Otherwise, you will quickly run into performance problems. But also, how
do you even go about building this world in your Godot editor? Even if you can solve the problem at
runtime by loading and unloading content, how will you extend that functionality to the editor? You
will find out very quickly that you cannot simply stuff all your content into a single World.tscn
file. In my experimentation over the years, I have found that a data-driven approach is the most
comfortable, reliable, and fits well with the Godot node structure.

This addon enables you to create a global grid that all your content is bound to. As your player (or other
origin object) travels around the world, the closest cells in grid-space are loaded around the player.
Cells are simply Godot scenes that contain game content. They are registered with the cellblock addon
throught the CellRegistry resource, and are keyed by a position on your game's grid. This means that
all local pieces of game content can be loaded as their own scene, and do not have to all live together
in a single world. Designing your game this way is potentially necessary if all your game content is too
large to exist in a single .tscn file, or is prohibitively slow in either the editor or in-game.

This addon has been tested with Godot 4.6 and should only be used with this version or greater. Using
Cellblock with an older version will likely break in strange ways due to recent changes in custom 
resource serialization. Keep in mind, Cellblock is still under active development, and there may be
breaking changes up until v1.0.0.

Thanks for watching, feel free to reach out to me on discord, or twitter, or reddit and I would
love for more community members to get involved! Thanks, goodbye

