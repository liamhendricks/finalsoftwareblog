---
title: Building Open world games with Cellblock
published: true
tag: summoning
---

{% include bilboard_image.html image-path="/assets/cellblockicon.png" %}
Get Cellblock here: [Cellblock](https://github.com/liamhendricks/cellblock/releases)

# Cellblock v0.4.0

About 6 months ago I decided to open source the first version of my data driven scene management
addon called [Cellblock](https://github.com/liamhendricks/cellblock/). Since then, a ton of work
has been done to improve the usability of the tool, brighten the documentation, and provide
stability to a very powerful workflow. As of right now, I have pushed v0.4.0, and I feel like the
addon is in a great place for general purpose use. So here is a simple tutorial on the basics of
getting up and running with Cellblock. I hope you enjoy!

# Tutorial text

Here is the text-based version for those of you that hate watching videos:

Hello everyone. It's been 6 months since I released the initial version of Cellblock, and now with
the release of v0.4.0, I'm back with a tutorial. Cellblock is a data driven scene management plugin
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

Today we're going to go over installation, configuration and an overview of the workflow. I'll also
talk a little bit about the ongoing development, and what to expect in the future.

This addon has been tested with Godot 4.6 and should only be used with this version. Using
Cellblock with an older version will likely break in strange ways due to recent changes in custom 
resource serialization. Keep in mind, Cellblock is still under active development, and there may be
breaking changes up until v1.0.0.

I'm going to be doing this tutorial alongside Terrain3D since it has become Godot's standard
terrain solution. It is not required, but I'm using it here.

First, in our world scene, we need to create a CellAnchor node. This provides access to the editor
tool, configuration options, and a visualization for where your cells live in world space. You
will need to create a cell registry resource, make it unique, and save it to disk. The cell
registry provides you a large number of configuration options to build your world, we'll go over
them one by one:

 - Load strategy dictates how the addon will load and manage cells at runtime. A low poly game
 may want to simply load all cells immediately and keep them in memory, but a more memory intensive
 game may wish to load everything from disk only as needed. We'll go with Async Load.
 - Cache size is the size of the in-memory cache of cells when using Async Loading. It will keep this
 number of cells in memory.
 - Grid size is the total size of your cell grid. I'll set this to the same size as my terrain.
 - Cell size is the size of each individual cell. I'll set this to 128. The cell size you choose for
 your game may require some experimentation!
 - Radius multiplier dictates the number of cells that will be kept in the scene. A radius of 1 for
 example, will load 27 cells in a 3d radius around the player. We'll keep this at 1.
 - Cell directory is the directory in your project where your cell scenes will be saved.
 - The base scene path is the cell scene that will be created. We are going to take a moment here
 to create our own cell scene that extends the base and then point to it. So now when we create
 cells, we will create one of this type, in the cell directory. This is highly recommended and i'll
 explain why later.
 - Iterations per frame sets the number of distance checks to do per frame. So the way that
 Cellblock knows which cells to keep in the scene, and which ones to discard, is done by simply
 checking the distance to the origin (player). It's not necessary to check the entire list every
 single frame, since your player will generally not be moving fast enough to need updates to the
 farthest cells immediately. So we can safely set this to 1 and not really notice a difference. Games
 with small cell sizes that need more responsive updates can set this higher.
 - Mutable process frames sets the number of mutable objects to be loaded per frame when we load a
 cell. We'll talk more about mutable objects later, so we'll just keep this at 1.

 We'll talk about saving and loading in a separate video along with some more advanced stuff, so for
now lets just leave the CellSave with it's defaults.

Next we need to write a bit of code in our world script. Now keep in mind that this is a trivial
example, and integrating cellblock into your project may require some more custom logic. But for
our purposes here, we just need to start the CellManager. Pass in your origin object. For me, this
will be the player, but you may want this to be a Camera, or some other node depending on your game.

Now were basically ready to start creating and editing our world.

When we click on the CellAnchor node in our scene, it will open up the dock window to show the
editor. Here is where we create, update and delete cells from the registry. Notice the spinners
move to their location in world space when I click them. The cell we create will be located here.

Ok lets go ahead and make our first cell. I'm going to create it here at 0,0,0, lets give it a name.
Now that this cell is created we can see it here in our editor. You'll notice that the scene has
also been saved to disk here. We can now edit this cell, so lets add some stuff. Now we can click
save, and clear. So we can also just go to this scene directly and make changes. Often times your
scenes don't even need to be edited alongside the terrain or another cell or whatever, so watch.
We can just save this, and when I load it, boom here's the stuff we just added. It will load
precisely like this in game as well. I'll just zoom through creating a few more cells so we can
see the loader in action.

[Run game and describe]

So that is truly all the basics you need to know. Now if we take a look at our cell_registry
resource file, you'll see that this is just references to scenes at a coordinate key. So now
your game content is just little chunks of data, and that's how you can think about it.

I hope this was enough to get people interested about the possibilities of building large
scale games with this approach. Obviously the addon is a work in progress, and you should expect
some jank, but the foundation works well, and I'll continue to improve and iterate!

Thanks for watching, feel free to reach out to me on discord, or twitter, or reddit and I would
love for more community members to get involved! Thanks, goodbye
