# quakemod_2025
Just notes on how to mod quake on 2025

# Editor

- Trenchbroom [https://trenchbroom.github.io/]

## Editor Config - Textures

- For showing textures, necessary to download quake wads: [https://www.slipseer.com/index.php?resources/original-vanilla-quake-wads.18/]
- Configure materials to display it (can simple do drag and drop with wad files)

## Editor Config - Models
- Open the game configuration you want to use (or create a new one for your Quake mod).
- Locate the section for entity definitions, which usually points to a .fgd file.
- Change the path to the .fgd file to point to the Quake 1 FGD file you downloaded.
- Alternatively, if the mod or community provides a base .fgd file, you can create a new file and use the @include directive to add the specific Quake FGD, such as @include "zhlt.fgd".

## Editor Config - Map Compilers
- Eric tools: [https://ericwa.github.io/ericw-tools/]

# Adding new models

- Need to export from Blender to MDL format
- Need to edit quakeC code and compile it to have the new model show in the editor
- vkQuake (so far) does not support misc_model entity

## Downloading quakeC code

- Look for progs 1.06 version [https://github.com/maddes-b/QuakeC-releases]
- The new quake remake works, but messages are now show due to localization changes and modern engines does not support it
- QuakeC compiler: https://www.fteqcc.org/

## Adding the new model - statue sample

- Modify progs.src and add at the end:
~~~
// List of QuakeC files for fteqcc
defs.qc
world.qc
statue.qc
~~~
- Add a new file named statue.qc:
~~~
/* Custom static statue entity */
void() misc_statue =
{
    precache_model ("progs/statue.mdl");
    setmodel (self, "progs/statue.mdl");

    // bounding box (adjust to your model size)
    setsize (self, '-16 -16 0', '16 16 64');

    self.solid = SOLID_BBOX;    // or SOLID_NOT if no collision
    self.movetype = MOVETYPE_NONE;
};
~~~
- now compile with: fteqcc progs.src
- create a folder inside quake for your mod, ie: mymod
- copy or mode progs.dat generated to mymod folder
- place your model at: mymod/progs/statue.mdl
- in the editor, add a entity to your map: classname: misc_statue
- compile your map and put it on the mod folder: mymod/maps/yourmap.bsp
- run quake: quake -game mymod +map yourmap

# Utils

- [https://valvedev.info/tools/pakexplorer/]
  
