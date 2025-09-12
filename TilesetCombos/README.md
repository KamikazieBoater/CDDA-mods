Combine tilesets


Do you like a specific tileset, but it hasn't been updated in a while and it's missing some sprites? Updating the tileset yourself or creating a custom tileset requires a bit of work, but here's a hack for how to layer tilesets upon each other by converting tilesets to mods, and then loading them in order.



Step-by-step guide


1. Copy the folders of the tilesets we want from \gfx to \data\mods.

2. Go in to the copied mod folder and delete layering.json (layering isn't supported in mods).

3. Rename tile_config.json to mod_tileset.json.

4. Open mod_tileset.json with a text editor and make the following chances:
	i. Wrap it in an array, that is put [ before the first character and ] after the last character.
	ii. Remove the "tile_info" field. It's typically located at the top and looks something like this:
"tile_info": [
    {
    "pixelscale": 1,
    "width": 32,
    "height": 32,
    "zlevel_height": 0,
    "iso": false,
    "retract_dist_min": -1.0,
    "retract_dist_max": 1.0
    }
],
	iii. Add these line where the "tile_info" field used to be:
    "type": "mod_tileset",
    "compatibility": ["UNDEAD_PEOPLE_BASE", "UNDEAD_PEOPLE", "MshockRealXotto", "MSX++DEAD_PEOPLE", "MSXotto+"],

This is the default "compatibility" for tilesets based on MShockXotto/UndeadPeople. If you use another base tileset, you can see it's name/id in the file \gfx\<TILESET NAME>\tileset.txt.

5. Create a file named modinfo.json in your mod folder and paste this into it:
[
  {
    "type": "MOD_INFO",
    "id": "tileset_any_unique_id_here",
    "name": "Ultica tiles as a mod",
    "authors": [ "ampersand55" ],
    "description": "Adds the tiles from Ultica to be used as a mod.",
    "category": "graphical",
    "dependencies": [ "dda" ]
  }
]

6. When you create a new world, add the mods under GRAPHICAL MODS with the tilesets with higher priority last. Remember to also create a tileset mod for the tileset you are currently using and put it last.



Some useful links

https://i-am-erk.github.io/CDDA-Tilesets/
https://docs.cataclysmdda.org/MODDING.html
https://docs.cataclysmdda.org/TILESET.html