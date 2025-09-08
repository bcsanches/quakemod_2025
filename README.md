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

